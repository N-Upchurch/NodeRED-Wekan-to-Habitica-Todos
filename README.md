# NodeRED Wekan to Habitica Todos
A Node-RED flow that integrates a Wekan Kanban Board and Habitica in two ways: 
* Creates Habitica todos when new Wekan cards are created
* "Scores" (marks complete and issues reward for) Habitica todos in Habitica when their matching cards are moved to a "Completed" column in Wekan.

![An image of the Node-RED UI populated with the "NodeRED Wekan to Habitica Todos" flow](https://upchur.ch/piwigo/i.php?/upload/2021/07/13/20210713191251-8f5d1f4e-xx.png)

## To Use: 
1. Install Node-RED & Wekan somewhere
2. Copy the contents of Node-REDFlowExport.json to your clipboard and import into your Node-RED instance
3. Complete setup per the instructions in the flow comment:
    * Create a webhook on a board in your Wekan instance. Set the URL to `yourNodeREDInstance.com/nodered/POSTcards`
    * Get the id of your 'completed' column in Wekan using the inspector. It will look something like this: `id="js-list-w3hpri5SCfJoE9CTD"`. We only need the last part, after `js-list-`.
    * Enter the list id in the `if` statement conditional of the `Build score task request Formula` node.
    * Fill in your credentials in the `Habitica Creds` node. ID & Client should both be your user ID, and key should be your API key. This information can be found in the [API](https://habitica.com/user/settings/api) section of your Habitica user settings.
    * Hit "Deploy," test, and enjoy.

## Further customization:
* Task difficulty can be set by changing the value of `"priority"` in the `Build create task request` node:

    |Value|Difficulty|
    |--|--|
    |0.1|Trivial|
    |1|Easy|
    |1.5|Medium|
    |2|Hard|

* Gold reward for completing the task can be set by adding the property `"value"` in the `Build create task request` node and setting to a positive number.
* Refer to the [Habitics API Docs](https://habitica.com/apidoc/#api-Task-CreateUserTasks) for more info.

## Contributing
If you'd like to enhance this flow's functionality or make it more flexible, please feel free to submit a PR!
