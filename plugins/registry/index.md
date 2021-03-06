---



copyright:

  years: 2017

lastupdated: "2017-12-08"


---

{:codeblock: .codeblock}
{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}

# {{site.data.keyword.registrylong_notm}} CLI
{: #containerregcli}

The {{site.data.keyword.registrylong}} CLI is a plug-in to manage your registry and its resources for your {{site.data.keyword.Bluemix_notm}} account.
{: shortdesc}

**Prerequisites**
* Before running the registry commands, log in to {{site.data.keyword.Bluemix_notm}}
 with the `bx login` command to generate an access token and authenticate your session.

To find out about how to use the {{site.data.keyword.registrylong_notm}} CLI, see [Getting started with {{site.data.keyword.registrylong_notm}}](../../../services/Registry/index.html).

<table summary="Manage {{site.data.keyword.registrylong_notm}}">
<caption>Table 1. Commands for managing {{site.data.keyword.registrylong_notm}}
</caption>
 <thead>
 <th colspan="5">Commands for managing the registry</th>
 </thead>
 <tbody>
 <tr>
 <td>[bx cr api](#bx_cr_api)</td>
 <td>[bx cr build](#bx_cr_build)</td>
 <td>[bx cr info](#bx_cr_info)</td>
 <td>[bx cr image-inspect](#bx_cr_image_inspect)</td>
 <td>[bx cr image-list (bx cr images)](#bx_cr_image_list)</td>
 </tr>
 <tr>
 <td>[bx cr image-rm](#bx_cr_image_rm)</td>
 <td>[bx cr login](#bx_cr_login)</td>
 <td>[bx cr namespace-add](#bx_cr_namespace_add)</td>
 <td>[bx cr namespace-list (bx cr namespaces)](#bx_cr_namespace_list)</td>
 <td>[bx cr namespace-rm](#bx_cr_namespace_rm)</td>
 </tr>
 <tr>
 <td>[bx cr plan](#bx_cr_plan)</td>
 <td>[bx cr plan-upgrade](#bx_cr_plan_upgrade)</td>
 <td>[bx cr quota](#bx_cr_quota)</td>
 <td>[bx cr quota-set](#bx_cr_quota_set)</td>
 <td>[bx cr region](#bx_cr_region)</td>
 </tr>
 <tr>
 <td>[bx cr region-set](#bx_cr_region_set)</td>
 <td>[bx cr token-add](#bx_cr_token_add)</td>
 <td>[bx cr token-get](#bx_cr_token_get)</td>
 <td>[bx cr token-list (bx cr tokens)](#bx_cr_token_list)</td>
 <td>[bx cr token-rm](#bx_cr_token_rm)</td>
 </tr><tr>
 <td>[bx cr vulnerability-assessment (bx cr va)](#bx_cr_va)</td>
 </tr>
 </tbody></table>



## bx cr api
{: #bx_cr_api}

Returns the details about the registry API endpoint that the commands are run against.

```
bx cr api
```
{: codeblock}


## bx cr build
{: #bx_cr_build}

Builds a Docker image in {{site.data.keyword.registrylong_notm}}.

```
bx cr build [--no-cache] [--pull] [--quiet | -q] [--build-arg KEY=VALUE ...] [--file FILE | -f FILE] --tag TAG DIRECTORY
```
{: codeblock}

**Parameters**
<dl>
<dt>DIRECTORY</dt>
<dd>The location of your build context, which contains your Dockerfile and prerequisite files.</dd>
<dt>--no-cache</dt>
<dd>(Optional)  If specified, cached image layers from previous builds are not used in this build.</dd>
<dt>--pull</dt>
<dd>(Optional) If specified, the base images are pulled even if an image with a matching tag already exists on the build host.</dd>
<dt>--quiet, -q</dt>
<dd>(Optional) If specified, the build output is suppressed unless an error occurs.</dd>
<dt> --build-arg KEY=VALUE</dt>
<dd>(Optional) Specify an additional build argument in the format 'KEY=VALUE'. Multiple build arguments can be specified by including this parameter multiple times. The value of each build argument is available as an environment variable when you specify an ARG line that matches the key in your Dockerfile.</dd>
<dt>--file FILE, -f FILE</dt>
<dd>(Optional)  If you use the same files for multiple builds, you can choose a path to a different Dockerfile. Specify the location of the Dockerfile relative to the build context. If not specified, the default is `PATH/Dockerfile`, where PATH is the root of the build context.</dd>
<dt>--tag TAG, -t TAG</dt>
<dd>The full name for the image that you want to build, which includes the registry URL and namespace.</dd>
</dl>


## bx cr info
{: #bx_cr_info}

Displays the name and the account of the registry that you are logged in to.

```
bx cr info
```
{: codeblock}


## bx cr image-inspect
{: #bx_cr_image_inspect}

Displays details about a specific image.

```
bx cr image-inspect [--format FORMAT] IMAGE [IMAGE...]
```
{: codeblock}

**Parameters**
<dl>
<dt>--format FORMAT</dt>
<dd>(Optional) Format the output elements by using a Go template. 

For more information, see [Formatting and filtering the CLI output for {{site.data.keyword.registrylong_notm}} commands](../../../services/Registry/registry_cli_reference.html#registry_cli_listing).

</dd>
<dt>IMAGE</dt>
<dd>The name of the image for which you want to get a report. You can inspect multiple images by listing each image in the command with a space between each name.

<p>To find the names of your images, run `bx cr image-list`. Combine the content of the Repository and Tag columns to create the image name in the format `repository:tag`. If a tag is not specified in the image name, the image that is tagged `latest` is inspected. </p> 

</dd>
</dl>


## bx cr image-list (bx cr images)
{: #bx_cr_image_list}

Displays all images in your {{site.data.keyword.Bluemix_notm}} account.

<p>**Note:** The image name is the combination of the content of the Repository and Tag columns in the format `repository:tag`. </p> 

```
 bx cr image-list [--no-trunc] [--format FORMAT] [-q, --quiet] [--restrict RESTRICTION] [--include-ibm] 
```
{: codeblock}

**Parameters**
<dl>
<dt>--no-trunc</dt>
<dd>(Optional) Do not truncate the image digests.</dd>
<dt>--format FORMAT</dt>
<dd>(Optional) Format the output elements by using a Go template. 

For more information, see [Formatting and filtering the CLI output for {{site.data.keyword.registrylong_notm}} commands](../../../services/Registry/registry_cli_reference.html#registry_cli_listing).

</dd>
<dt>-q, --quiet</dt>
<dd>(Optional) Each image is listed in the format: `repository:tag`</dd>
<dt>--restrict RESTRICTION</dt>
<dd>(Optional) Limit the output to display only images in the specified namespace or namespace and repository. </dd>
<dt>--include-ibm</dt>
<dd>(Optional) Includes {{site.data.keyword.IBM_notm}}-provided public images in the output. Without this option, by default private images only are listed.</dd>
</dl>



## bx cr image-rm
{: #bx_cr_image_rm}

Deletes one or more specified images from your registry.

```
bx cr image-rm IMAGE [IMAGE...]
```
{: codeblock}

**Parameters**
<dl>
<dt>IMAGE</dt>
<dd>The name of the image for which you want to get a report. You can delete multiple images at the same time by listing each image in the command with a space between each name.

<p>To find the names of your images, run `bx cr image-list`. Combine the content of the Repository and Tag columns to create the image name in the format `repository:tag`. If a tag is not specified in the image name, the image that is tagged `latest` is deleted by default.</p> 

</dd>
</dl>


## bx cr login
{: #bx_cr_login}

This command runs the `docker login` command against the registry. The `docker login` command is required to be able to run the `docker push` or `docker pull` commands for the registry. This command is not required to run other `bx cr` commands. If Docker is not installed, this command returns an error message.

```
bx cr login
```
{: codeblock}


## bx cr namespace-add
{: #bx_cr_namespace_add}

Adds a namespace to your {{site.data.keyword.Bluemix_notm}} account.

```
bx cr namespace-add NAMESPACE
```
{: codeblock}

**Parameters**
<dl>
<dt>NAMESPACE</dt>
<dd>The namespace you want to add. The namespace must be unique across all {{site.data.keyword.Bluemix_notm}} accounts in the same region.</dd>
</dl>


## bx cr namespace-list (bx cr namespaces)
{: #bx_cr_namespace_list}

Displays all namespaces that are owned by your {{site.data.keyword.Bluemix_notm}} account.

```
bx cr namespace-list
```
{: codeblock}


## bx cr namespace-rm
{: #bx_cr_namespace_rm}

Removes a namespace from your {{site.data.keyword.Bluemix_notm}} account. Images in this namespace are deleted when the namespace is removed.

```
bx cr namespace-rm NAMESPACE
```
{: codeblock}

**Parameters**
<dl>
<dt>NAMESPACE</dt>
<dd>The namespace that you want to remove.</dd>
</dl>


## bx cr plan
{: #bx_cr_plan}

Displays your pricing plan.

```
bx cr plan
```
{: codeblock}


## bx cr plan-upgrade
{: #bx_cr_plan_upgrade}

Upgrades you to the standard plan.

For information about plans, see [Registry plans](../../../services/Registry/registry_overview.html#registry_plans).

```
bx cr plan-upgrade [PLAN]
```
{: codeblock}

**Parameters**
<dl>
<dt>PLAN</dt>
<dd>The name of the pricing plan that you want to upgrade to. If PLAN is not specified, the default is `standard`.</dd>
</dl>


## bx cr quota
{: #bx_cr_quota}

Displays your current quotas for traffic and storage, and usage information against those quotas.

```
bx cr quota
```
{: codeblock}


## bx cr quota-set
{: #bx_cr_quota_set}

Modify the specified quota.

```
bx cr quota-set [--traffic TRAFFIC] [--storage STORAGE]
```
{: codeblock}

**Parameters**
<dl>
<dt>--traffic TRAFFIC</dt>
<dd>(Optional) Changes your traffic quota to the specified value in megabytes. The operation fails if you are not authorized to set traffic, or if you set a value that exceeds your current pricing plan.</dd>
<dt>--storage STORAGE</dt>
<dd>(Optional) Changes your storage quota to the specified value in megabytes. The operation fails if you are not authorized to set storage quotas, or if you set a value that exceeds your current pricing plan.</dd>
</dl>


## bx cr region
{: #bx_cr_region}

Displays the targeted region and the registry.

```
bx cr region
```
{: codeblock}

For more information, see [Regions](../../../services/Registry/registry_overview.html#registry_regions).


## bx cr region-set
{: #bx_cr_region_set}

Set a target region for the {{site.data.keyword.registrylong_notm}} commands. To list the available regions, run the command with no parameters.

```
bx cr region-set [REGION]
```
{: codeblock}

**Parameters**
<dl>
<dt>REGION</dt>
<dd>(Optional) The name of your target region, for example, `us-south`. 

For more information, see [Regions](../../../services/Registry/registry_overview.html#registry_regions).

</dd>
</dl>


## bx cr token-add
{: #bx_cr_token_add}

Adds a token that you can use to control access to a registry.

```
bx cr token-add [--description DESCRIPTION] [-q, --quiet] [--non-expiring] [--readwrite]
```

{: codeblock}


**Parameters**
<dl>
<dt>--description DESCRIPTION</dt>
<dd>(Optional) Specifies the value as a description for the token, which is displayed when you run `bx cr token-list`. If your token is created automatically by {{site.data.keyword.containerlong_notm}}, the description is set to your Kubernetes Cluster name. In this case, the token is removed automatically when your cluster is removed.</dd>
<dt>-q, --quiet</dt>
<dd>(Optional) Displays the token only, without any surrounding text.</dd>
<dt>--non-expiring</dt>
<dd>(Optional) Creates a token with access that does not expire. Without this parameter set, access from a token expires after 24 hours by default.</dd>
<dt>--readwrite</dt>
<dd>(Optional) Creates a token that grants read and write access. Without this option, access is read-only by default.</dd>
</dl>


## bx cr token-get
{: #bx_cr_token_get}

Retrieve the specified token from the registry.

```
bx cr token-get TOKEN
```

{: codeblock}

**Parameters**
<dl>
<dt>TOKEN</dt>
<dd>(Optional) The unique identifier of the token that you want to retrieve.</dd>
</dl>


## bx cr token-list (bx cr tokens)
{: #bx_cr_token_list}

Displays all tokens that exist for your {{site.data.keyword.Bluemix_notm}} account.

```
bx cr token-list --format FORMAT
```
{: codeblock}

**Parameters**
<dl>
<dt>--format FORMAT</dt>
<dd>(Optional) Format the output elements by using a Go template. 

For more information, see [Formatting and filtering the CLI output for {{site.data.keyword.registrylong_notm}} commands](../../../services/Registry/registry_cli_reference.html#registry_cli_listing).

</dd>
</dl>


## bx cr token-rm
{: #bx_cr_token_rm}

Remove one or more specified tokens.

```
bx cr token-rm TOKEN [TOKEN...]
```
{: codeblock}

**Parameters**
<dl>
<dt>TOKEN</dt>
<dd>(Optional) TOKEN can be either the token itself, or the unique identifier of the token, as shown in `bx cr token-list`. Multiple tokens can be specified and they must be separated by a space.</dd>
</dl>


## bx cr vulnerability-assessment (bx cr va)
{: #bx_cr_va}

View a vulnerability assessment report for your images.

```
bx cr vulnerability-assessment [--extended | -e] [--vulnerabilities | -v] [--configuration-issues | -c] [--output FORMAT | -o FORMAT] IMAGE [IMAGE...] 
```
{: codeblock}

**Parameters**
<dl>
<dt>IMAGE</dt>
<dd>The name of the image for which you want to get a report. The report tells you whether the image has any known package vulnerabilities. You can request reports for multiple images at the same time by listing each image in the command with a space between each name.

<p>To find the names of your images, run `bx cr image-list`. Combine the content of the Repository and Tag columns to create the image name in the format `repository:tag`. If a tag is not specified in the image name, the report assesses the image that is tagged `latest`. </p> 

<p>The following operating systems are supported:

<ul>

<li>Alpine</li>
<li>CentOS</li>
<li>Debian</li>
<li>Red Hat Enterprise Linux (RHEL)</li>
<li>Ubuntu</li>
</ul>

</p>

For more information, see [Managing image security with Vulnerability Advisor](../../../services/va/va_index.html).

</dd>
<dt>--output FORMAT, -o FORMAT</dt>
<dd>(Optional) The command output is returned in the chosen format. The default format is `text`. The following formats are supported:

<ul>

<li>`text`</li>
<li>`json`</li>
</ul>

</dd>
<dt>--vulnerabilities, -v</dt>
<dd>(Optional) The command output is restricted to show vulnerabilities only.</dd>
<dt>--configuration-issues, -c</dt>
<dd>(Optional) The command output is restricted to show configuration issues only.</dd>
<dt>--extended, -e </dt>
<dd>(Optional) The command output shows additional information about fixes for vulnerable packages.</dd>

</dl>

