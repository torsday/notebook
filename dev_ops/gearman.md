# Gearman

*From: [GearmanHQ](http://gearmanhq.com/help/getting-started)*

> A generic application framework for doing work in the background, spanning different machines, networks, and workers, each suited to preforming a specific job or set of jobs. Gearman itself acts as the central nervous system: jobs can come in from a variety of source, and workers can be on several machines and running in several different langauges.

![Gearman Flowchart](https://upload.wikimedia.org/wikipedia/en/c/c5/Gearman_Stack.png)

---

## Definitions

### Worker

The thing that ultimately completes the tasks.

### Client

Request that work be completed by somebody.

> The client is responsible for creating the jobs in the job queue and has two basic modes of operation, that is, synchronous or asynchronous.

> In **synchronous** mode, the client submits the job to the manager and waits for the job to be picked up, worked on, and completed interactively. The client does not disconnect from the server and remains connected throughout the life span of the job. This mode is useful for jobs where the results of the job are needed by the client itself.

> In **asynchronous** mode, the client effectively operates in a "fire and forget" mode where the job is submitted to the manager and there is an implicit contract that the job will be completed at some point in the future. These types of jobs tend to be longer-running tasks that would block the client for a long time; by using this mode, the client is free to do other things such as submit more jobs, or perform other tasks.

### Manager (Server)

Responsible for accepting jobs from clients, then handing those jobs out to workers.

### Workload

The serializable object passed back and forth.

---

## Example Code

### Client

```ruby
#!/usr/bin/env ruby
require 'rubygems'
require 'gearman'


# Create a client that connects to the local manager
client = Gearman::Client.new('127.0.0.1:4730')

# Create a set of tasks that the client processes (this is unique to # the Ruby client, and required for us to wait for them to complete)
taskset = Gearman::TaskSet.new(client)

# Create an actual task for the 'reverse_string' queue with 'reverse this string' as the data to be processed by the worker
task = Gearman::Task.new("reverse_string", "reverse this string")

# In the Ruby client, tasks have an 'on_complete' callback that lets you execute some code with the result of a job
task.on_complete {|d| puts d }

# Add the task to the set of tasks to process (this is what submits the job)
puts "Submitting job..."
taskset.add_task(task)

# Wait 86,400 seconds for a response (all day)
puts "Waiting for a response..."
taskset.wait(86400)
```

### worker

```ruby
require 'rubygems'
require 'gearman'

servers = ['localhost:4730']

# Connect to our list of servers (only one for now)
w = Gearman::Worker.new(servers)

# The Worker class has a method, add_abilitywhich takes
# two arguments, the queue to register and a block that
# is the code to execute for each job taken
w.add_ability('reverse_string') do |data, job|
      puts "Got work!"
      # Dump out what we got
      puts "Job: #{job.inspect} Data: #{data.inspect}"
      # Reverse the data portion
      result = data.reverse
      puts "Reverse: #{result} "
      # The return value of the block is what gets sent back
      # to the manager as the response data for this job
      result
end

# Execute only one unit of work
w.work
```

### Running it

```bash
[user@host]% ruby client.rb
Submitting job...
Waiting for a response...
```

```ruby
[user@host]% ruby worker.rb
Got work!
Job: #<Gearman::Worker::Job:0x0000010112f820 @socket=#<TCPSocket:fd 5>, @handle="e518b247-e7a5-4470-a9ff-0940356dab51"> Data: "reverse this string"
Reverse: gnirts siht esrever
```

#### Backgrounding

```ruby
require 'rubygems'
require 'gearman'

servers = ['localhost:4730']
# Connect our client
client = Gearman::Client.new(servers)

# Generate a task with the background property being set
task = Gearman::Task.new({'background_job', 'data',
:background => true })

# Submit a job via the client
client.do_task(task)
```

---

## References

-   <http://gearman.org/getting-started/>
-   [Jay Paroline: How Grooveshark Uses Gearman](http://wanderr.com/jay/how-grooveshark-uses-gearman/2011/03/27)
