---
 
copyright:
  years: 2015, 2019
lastupdated: "2019-02-28"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

<!-- This template is for introducing a command-line interface (CLI). It is a reference template intended to document productive use of the CLI. It is not intended for task information. -->

<!-- Name your file `offering-cli-name.md`, for example, `auto-scaling-cli.md` is the file name of the Auto-Scaling CLI reference topic. Delete content examples and coding that you are not using for your offering. -->


# {{site.data.keyword.ibmwatson_notm}} {{site.data.keyword.pm_short}} CLI
<!-- Insert your CLI name into topic title above. -->
{: #machine-learning-cli}
<!-- Provide an appropriate ID above -->


<!-- Short description: REQUIRED
The short description section should include one to two sentences describing why a developer would want to use this cli. This should be conversational style. For search engine optimization, include your offering's CLI name. Keep the {: shortdesc} after the first paragraph so that the framework renders it properly.

Example: -->

You can use the {{site.data.keyword.pm_full}} CLI (plugin name: `machine-learning`) to train and deploy models, as well as manage objects in your repository from a command line on you computer.
{:shortdesc} 


<!-- Prerequisites/Authorization/Environment: OPTIONAL
The section should lists all the prerequisites/authorization/environment that are required to use the CLI commands. Or give a brief introduction to the prerequisites/authorization/environment that the CLI commands might use. Use **Note** to call out this section.
Example: -->

**Notes**
- Instructions for setting up the CLI on your local computer are here: [Setting up the CLI](https://dataplatform.cloud.ibm.com/docs/content/analyze-data/ml_dlaas_environment.html)
- Explanations for key terms are here: [Terminology](https://dataplatform.cloud.ibm.com/docs/content/analyze-data/ml-terminology.html)

<p>&nbsp;</p>

In May 2018, the {{site.data.keyword.Bluemix_notm}} CLI commands changed from `bluemix` and `bx` to `ibmcloud`. So, for example, the command `bx ml help` became `ibmcloud ml help`.  You can still use the `bluemix` and `bx` CLI commands until they are removed in the future.  If you have scripts that use the `bluemix` and `bx` commands, update those scripts to use `ibmcloud` (or consider other strategies, such as using command aliases.)
{: tip}

<p>&nbsp;</p>

<!-- Commands index: REQUIRED
Use a table to list out all the commands in alphabetic order so that commands information is easy to scan and locate. Add a link to the anchor of each command.  
Use "<CLI_name> commands index" as the section title. 
Sort the command in alphabetic order from left to right across the columns in each row, and then by successive rows and columns.
Include no more than 5 columns for a table. 
If there are a great many commands, to make it easy to retrieve specific commands, you can add several index tables. Group the commands by functions or other similar characteristics, and then make each group a table, with the commands listed in alphabetic order across the columns in each row. 
Examples: -->


## {{site.data.keyword.ibmwatson_notm}} {{site.data.keyword.pm_short}} CLI commands index
{: #commands_index}

You can specify one of the following commands:

<table summary="Commands">
<caption>Table 1. Commands</caption>  
 <thead>
 <th colspan="5">Commands</th>
 </thead>
 <tbody> 
 <tr> 
 <td>[cancel](#cancel)</td> 
 <td>[delete](#delete)</td> 
 <td>[deploy](#deploy)</td>
 <td>[experiments](#experiments)</td>
 </tr>
 <tr> 
 <td>[generate-manifest](#generate-manifest)</td>
 <td>[help     ](#help)</td>
 <td>[libraries](#libraries)</td>
 <td>[list     ](#list)</td>
 </tr>
 <tr> 
 <td>[models  ](#models)</td>
 <td>[monitor ](#monitor)</td>
 <td>[runtimes](#runtimes)</td>
 <td>[score   ](#score)</td>
 </tr>
 <tr> 
 <td>[show   ](#show)</td>
 <td>[store  ](#store)</td>
 <td>[train  ](#train)</td>
 <td>[version](#version)</td>
 </tr>
 </tbody> 
</table> 

<p>&nbsp;</p>
 
 
<!-- Command entries: REQUIRED
Directly use the command name as title.  Add an anchor ID, for example, {: #login}, for each command entry, so that you can link to the command entry from the index table. Include a sentence to briefly introduce the command, such as what does this command do. 

Command syntax: Add the command syntax by using three backticks ahead of and after the syntax (```). 

Command prerequisites/authorization/environment: Prerequisites/authorization/environment that are required to use this command. Use the ** ** markup to highlight the word prerequisites/authorization/environment. 

Command Options: Use the ** ** markup markup to highlight the word "Command options". Use a definition list to introduce the options. Make one option one list item. 
				 
Examples: Use the ** ** markup to highlight the word "Examples".
          - Include one sentence to describe each example.
		   - Add the example by using three backticks ahead of and after the example (```)
		   - For copyable code snippet, multi-line, include {: codeblock} following the last set of backticks. A copy button will display in framework in output.
          - For copyable command, single line, include {: pre} following the last set of backticks. When displayed, it will show "$" at the beginning of the command example and a copy button, but the copy button will include just the command example.
 
Examples:

## login
{: #login}

Use this command to log in to {{site.data.keyword.Bluemix_notm}}. 

```
cloud-cli login [userID] [pw]
```
**Prerequisites**: None.

**Command options**:  

   <dl>
   <dt>userID</dt>
   <dd>The {{site.data.keyword.Bluemix_notm}} user ID.</dd>
   <dt>pw</dt>
   <dd>The user's password for {{site.data.keyword.Bluemix_notm}}.</dd>
    </dl>

**Examples**:
-->

<!----------------------------------------------------------------------------- cancel -->
## cancel
{: #cancel}

Cancel training a model.

```
ibmcloud ml cancel training-runs <model-id>
```
<p>&nbsp;</p>


<!----------------------------------------------------------------------------- delete -->
## delete
{: #delete}

Delete an object from the repository:
- Training definition
- Training run
- Experiment
- Experiment run
- Model
- Deployment
- Library
- Runtime

Syntax for different types of objects:
```
ibmcloud ml delete training-definitions <training-definition-id>
ibmcloud ml delete training-runs <training-run-id>
ibmcloud ml delete experiments <experiment-id>
ibmcloud ml delete experiment-runs <experiment-id> <experiment-run-id>
ibmcloud ml delete models <model-id>
ibmcloud ml delete deployments <model-id> <deployment-id>
ibmcloud ml delete libraries <library-id>
ibmcloud ml delete runtimes <runtime-id>
```

where the object identifier (such as &lt;model-id>) specifies the object to delete from the repository.

<p>&nbsp;</p>


<!----------------------------------------------------------------------------- deploy -->
## deploy
{: #deploy}

Deploy a model that is stored in the repository.

Two types of deployment are supported:
- Web service
- Batch deployment

Syntax for deploying a web service:
```
ibmcloud ml deploy <model-id> <deployment-name>
```

Syntax for a batch deployment:
```
ibmcloud ml deploy -b <model-id> <deployment-name> <manifest-file-name>
```

where:
- &lt;model-id> is the identifier of a model that is already stored in the repository.
- &lt;deployment-name> is a name you choose for the deployment object.
- &lt;manifest-file-name> is the absolute or relative path and name of a JSON- or YAML-formatted file that specifies details of the batch deployment.

<p>&nbsp;</p>


<!----------------------------------------------------------------------------- experiments -->
## experiments
{: #experiments}

Run or update an experiment that is stored in the repository.

Syntax for running an experiment:
```
ibmcloud ml experiments run <experiment-id>
```

Syntax for updating an experiment:
```
ibmcloud ml experiments update <experiment-id> <manifest-file-name>
```

where:
- &lt;experiment-id> is the identifier of an experiment that is already stored in the repository.
- &lt;manifest-file-name> is the absolute or relative path and name of a JSON- or YAML-formatted file that specifies details of the experiment.

<p>&nbsp;</p>


<!----------------------------------------------------------------------------- generate-manifest -->
## generate-manifest
{: #generate-manifest}

Generate a sample JSON manifest file.

With many machine learning commands, you specify execution or configuration details in a JSON- or YAML-formatted file , called a *manifest file*.  The `generate-manifest` command generates a template JSON manifest file.  You can use the generated manifest file template as a base for creating your own manifest files: update the template for use in JSON format, or convert the template to YAML.

Syntax for generating a manifest file for different scenarios:
```
ibmcloud ml generate-manifest <manifest-file-type>
```

where &lt;manifest-file-type> is one of the values in table 2:

<table summary="Manifest file types" <caption>Table 2. Manifest file types</caption>  
<thead>
<th><manifest-file-type> value</th>
<th>Scenario</th>
</thead>
<tbody>
<tr>
<td>`training-definitions`</td>
<td>Create a template manifest file for use with this command:<br/>`ibmcloud ml store training-definitions`</td>
</tr>
<tr>
<td>`training-runs`</td>
<td>Create a template manifest file for use with these commands:<br/>`ibmcloud ml train`<br/>`ibmcloud ml train training-definitions`</td>
</tr>
<tr>
<td>`store-training-runs`</td>
<td>Create a template manifest file for use with this command:<br/>`ibmcloud ml store training-runs`</td>
</tr>
<tr>
<td>`experiments`</td>
<td>Create a template manifest file for use with this command:<br/>`ibmcloud ml store experiments`</td>
</tr>
<tr>
<td>`update-experiments`</td>
<td>Create a template manifest file for use with this command:<br/>`ibmcloud ml experiments update`</td>
</tr>
<tr>
<td>`libraries`</td>
<td>Create a template manifest file for use with this command:<br/>`ibmcloud ml store libraries`</td>
</tr>
<tr>
<td>`update-libraries`</td>
<td>Create a template manifest file for use with this command:<br/>`ibmcloud ml libraries update`</td>
</tr>
<tr>
<td>`runtimes`</td>
<td>Create a template manifest file for use with this command:<br/>`ibmcloud ml store runtimes`</td>
</tr>
<tr>
<td>`update-runtimes`</td>
<td>Create a template manifest file for use with this command:<br/>`ibmcloud ml runtimes update`</td>
</tr>
<tr>
<td>`batch`</td>
<td>Create a template manifest file for use with this command:<br/>`ibmcloud ml deploy -b`</td>
</tr>
</tbody>
</table>

<p>&nbsp;</p>


<!----------------------------------------------------------------------------- help -->
## help
{: #help}

Show command help.

```
ibmcloud ml help [ <command> ]
```

where &lt;command> is one of the other commands listed in this topic.

<p>&nbsp;</p>


<!----------------------------------------------------------------------------- libraries -->
## libraries
{: #libraries}

Update a library that is stored in the repository, or download a library from the repository.

Syntax for updating the metadata for a library that is already stored in the repository:
```
ibmcloud ml libraries update <library-id> <manifest-file-name>
```

Syntax for updating the custom Python distribution package of a library that is already stored in the repository:
```
ibmcloud ml libraries update-content <library-id> <custom-package-file-name>
```

Syntax for downloading a library from the repository to the current directory:
```
ibmcloud ml libraries download <library-id>
```


where:
- &lt;library-id> is the identifier of a library that was stored in the repository with the command: `ibmcloud ml store libraries`.
- &lt;manifest-file-name> is the absolute or relative path and name of a JSON- or YAML-formatted file that specifies details of the update.
- &lt;path-to-content> is the absolute or relative path and name of a custom Python distribution package .zip file.

<p>&nbsp;</p>


<!----------------------------------------------------------------------------- list -->
## list
{: #list}

List objects that are stored in the repository.

Syntax for listing different types of objects:
```
ibmcloud ml list training-definitions
ibmcloud ml list training-runs
ibmcloud ml list training-runs <experiment-id> <experiment-run-id>
ibmcloud ml list experiments
ibmcloud ml list models
ibmcloud ml list deployments
ibmcloud ml list deployments <model-id>
ibmcloud ml list libraries
ibmcloud ml list runtimes
ibmcloud ml list experiment-runs <experiment-id>
```

where the object identifier (such as &lt;model-id>) specifies an object associated with the objects to list.

<p>&nbsp;</p>


<!----------------------------------------------------------------------------- models -->
## models
{: #models}

Download a model from the repository to the current directory.

```
ibmcloud ml models download <model-id>
```

where &lt;model-id> specifies the model to download.

<p>&nbsp;</p>


<!----------------------------------------------------------------------------- monitor -->
## monitor
{: #monitor}

Show metrics or log messages of a training run or experiment.

Syntax for training runs:
```
ibmcloud ml monitor training-runs <training-run-id> [ metrics | logs [ last <number-of-lines> ] ]
```

Syntax for experiments:
```
ibmcloud ml monitor experiments <experiment-id> <experiment-run-id> [ metrics | logs ]
```

where:
- The object identifier (such as &lt;training-run-id>) specifies the object for which to retrieve metrics or logs.
- &lt;number-of-lines> is a number you choose.  If you specify this optional argument, only up to the specified number of lines of the most recent messages will be shown.

<p>&nbsp;</p>


<!----------------------------------------------------------------------------- runtimes -->
## runtimes
{: #runtimes}

Update the metadata of a runtime in the repository, upload new content for a runtime in the repository, or download a runtime that is stored in the repository.

Syntax for updating the metadata of a runtime that is already stored in the repository:
```
ibmcloud ml runtimes update <runtime-id> <manifest-file-name>
```

Syntax for uploading a Conda YAML file (for Python) or a Scala build definition file for a runtime:
```
ibmcloud ml runtimes upload <runtime-id> <sbt-yaml-file-name>
```

Syntax for downloading a runtime to the current directory:
```
ibmcloud ml runtimes download <runtime-id>
```


where:
- &lt;runtime-id> is the identifier of a runtime that was stored in the repository with the command: `ibmcloud ml store runtimes`.
- &lt;manifest-file-name> is the absolute or relative path and name of a JSON- or YAML-formatted file that specifies details of the update.
- &lt;sbt-yaml-file-name> is the absolute or relative path and name of a Conda YAML file (for Python) or a Scala build definition file.

<p>&nbsp;</p>


<!----------------------------------------------------------------------------- score -->
## score
{: #score}

Analyze data (for example, classify the data, or make a prediction from the data) using a model deployment in the repository.  

```
ibmcloud ml score <data-file-name>
```

where &lt;data-file-name> specifies the absolute or relative path and name of a JSON-formatted file that specifies the model identifier, the deployment identifier, and the data to be analyzed (the *payload*.)

**Example**

Sample data file JSON content for a hypothetical model that has been trained to predict the chance of rain based on three weather characteristics:
```
{
   "modelId"      : "a8379aaa-ea31-4c22-824d-89a01315dd6d",
   "deploymentId" : "9d6a656c-e9d4-4d89-b335-f9da40e52179",
   "payload"      : {
                       "fields" : [ "temperature", "windspeed", "iscloudy" ],
                       "values" : [ 15, 50, "F" ]
                     }
}
```

<p>&nbsp;</p>


<!----------------------------------------------------------------------------- show -->
## show
{: #show}

Get detailed information about objects that are stored in the repository.

Syntax for getting detailed information about different types of objects:
```
ibmcloud ml show training-definitions <training-definition-id>
ibmcloud ml show training-runs <training-run-id>
ibmcloud ml show experiments <experiment-id> <experiment-run-id>
ibmcloud ml show experiment-runs <experiment-id> <experiment-run-id>
ibmcloud ml show models <model-id>
ibmcloud ml show deployments <model-id> <deployment-id>
ibmcloud ml show libraries <library-id>
ibmcloud ml show runtimes <runtime-id>
```

where the object identifier (such as &lt;model-id>) specifies an object that is stored in the repository.

<p>&nbsp;</p>


<!----------------------------------------------------------------------------- store -->
## store
{: #store}

Store an object in the repository.

Syntax for storing different types of objects:
```
ibmcloud ml store training-definitions <training-definition-file-name> <manifest-file-name>
ibmcloud ml store training-runs <training-run-id> [ <manifest-file-name> ]
ibmcloud ml store experiments <manifest-file-name>
ibmcloud ml store <model-file-name> <manifest-file-name>
ibmcloud ml store libraries <library-file-name> <manifest-file-name>
ibmcloud ml store runtimes <manifest-file-name>
```

where:
- &lt;model-file-name> is the absolute or relative path and name of a file in tar.gz format that contains model-building code.
- &lt;manifest-file-name> is the absolute or relative path and name of a JSON- or YAML-formatted file that specifies metadata for storing the object.
- &lt;library-file-name> is the absolute or relative path and name of a file in .zip format that contains a custom library.
- &lt;training-definition-file-name> is the absolute or relative path and name of a training definition file in .zip format.

<p>&nbsp;</p>


<!----------------------------------------------------------------------------- train -->
## train
{: #train}

Start a training run to train a model.

Syntax for training a model by passing model-building code:
```
ibmcloud ml train <model-building-file-name> <manifest-file-name>
```

Syntax for training a model by using a training definition:
```
ibmcloud ml train training-definitions <training-definition-id> <training-definition-version-id> <manifest-file-name>
```

where:
- &lt;model-building-file-name> is the absolute or relative path and name of a file in .zip format that contains model-building code.
- &lt;manifest-file-name> is the absolute or relative path and name of a JSON- or YAML-formatted file that specifies model and training details.
- &lt;training-definition-id> is the identifier generated when you stored the training definition.
- &lt;training-definition-version-id> is version identifier generated when you stored the training definition.

<p>&nbsp;</p>


<!----------------------------------------------------------------------------- version -->
## version
{: #version}

View the Git commit hash and build time of the currently installed machine learning CLI.

```
ibmcloud ml version
```

<p>&nbsp;</p>


