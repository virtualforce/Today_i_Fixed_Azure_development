# Problem
Creating and configuring an Event Hub and publish events to Event Hubs


# Environment
To use Event Hub make sure you have Microsoft Azure subscription, if not create a free account before you begin.

# Solution
## Follow the following steps to resolve this error


## Step 1
Type Event Hub in the search box and select Event Hub Resource and click create, then select your resource group, add Namespace name and select the region in which you want to create the resource.
Then click on Review + Create.

![Image 1](https://github.com/jam-ayub/Today_i_Fixed_Azure_development/assets/72668520/22ab74cf-d29e-4be2-a98d-b4c698e99e90)


## Step 2
After the deployement is complete go to your resource and click on +Event Hub.
Then add required settings with partition count and retention time.
You can confirm it by going to the Event Hubs blade under Enities section.

![Image 2](https://github.com/jam-ayub/Today_i_Fixed_Azure_development/assets/72668520/9eb0c997-2d5a-4b87-a307-56013eb0f377)

## Step 3
Under Shared access policies, create a policy with MANAGE permissions by selecting + Add. 
Give the policy a name, check MANAGE, and then select Create.

![Image 3](https://github.com/jam-ayub/Today_i_Fixed_Azure_development/assets/72668520/94b433b2-5785-498b-8513-c603e31f468a)

## Step 4
Click on the SAS Policy that you created and then select the copy button for the CONNECTION STRING – PRIMARY KEY entity. Paste the CONNECTION STRING – PRIMARY KEY entity into Notepad.

![Image 4](https://github.com/jam-ayub/Today_i_Fixed_Azure_development/assets/72668520/dbf8064e-4613-4b56-b229-c07df8a0c846)

## Step 5
In order to Publish events to Event Hubs use the the following code.

```
var connectionStr = "Connection String";
var eventHubName = "Event Hub Name";

await using (var producer = new EventHubProducerClient(connectionString, eventHubName))
{
    using EventDataBatch eventBatch = await producer.CreateBatchAsync();
    eventBatch.TryAdd(new EventData(new BinaryData("First")));
    eventBatch.TryAdd(new EventData(new BinaryData("Second")));

    await producer.SendAsync(eventBatch);
}
```
