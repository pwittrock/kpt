---
title: "API Reference"
linkTitle: "API Reference"
weight: 40
description: >
    Overview of kpt declarative APIs
---

<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>title</title>
<link rel="shortcut icon" href="favicon.ico" type="image/vnd.microsoft.icon">
<!-- Latest compiled and minified CSS -->
</head>
<body>
<div id="wrapper">
<div id="sidebar-wrapper" class="side-nav"><ul class="sidebar-nav"><li class="nav-level-1"><a href="#deployment-v1beta1" class="nav-item">Deployment v1beta1</a></li><li class="nav-level-2"><a href="#write-operations-3" class="nav-item">Write Operations</a></li><li class="nav-level-2"><a href="#create-4" class="nav-item">Create</a></li><li class="nav-level-2"><a href="#replace-9" class="nav-item">Replace</a></li></ul></div>
<div id="page-content-wrapper" class="body-content container-fluid"><h1 id="deployment-v1beta1">Deployment v1beta1</h1>
<table>
<thead>
<tr>
<th>Group</th>
<th>Version</th>
<th>Kind</th>
</tr>
</thead>
<tbody>
<tr>
<td>Extensions</td>
<td>v1beta1</td>
<td>Deployment</td>
</tr>
</tbody>
</table>
<blockquote class="code-block kubectl">
<p> Deployment Config to run 3 nginx instances (max rollback set to 10 revisions).</p>
</blockquote>
<pre class="code-block kubectl"><code class="lang-yaml"><span class="hljs-attr">apiVersion:</span> <span class="hljs-string">extensions/v1beta1</span>
<span class="hljs-attr">kind:</span> <span class="hljs-string">Deployment</span>
<span class="hljs-attr">metadata:</span>
  <span class="hljs-attr">name:</span> <span class="hljs-string">deployment-example</span>
<span class="hljs-attr">spec:</span>
  <span class="hljs-attr">replicas:</span> <span class="hljs-number">3</span>
  <span class="hljs-attr">revisionHistoryLimit:</span> <span class="hljs-number">10</span>
  <span class="hljs-attr">template:</span>
    <span class="hljs-attr">metadata:</span>
      <span class="hljs-attr">labels:</span>
        <span class="hljs-attr">app:</span> <span class="hljs-string">nginx</span>
    <span class="hljs-attr">spec:</span>
      <span class="hljs-attr">containers:</span>
      <span class="hljs-bullet">-</span> <span class="hljs-attr">name:</span> <span class="hljs-string">nginx</span>
        <span class="hljs-attr">image:</span> <span class="hljs-string">nginx:1.10</span>
</code></pre>
<p>Deployment enables declarative updates for Pods and ReplicaSets.</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Schema</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>metadata</td>
<td><a href="#objectmeta-v1">ObjectMeta</a></td>
<td>Standard object metadata.</td>
</tr>
<tr>
<td>spec</td>
<td><a href="#deploymentspec-v1beta1">DeploymentSpec</a></td>
<td>Specification of the desired behavior of the Deployment.</td>
</tr>
<tr>
<td>status</td>
<td><a href="#deploymentstatus-v1beta1">DeploymentStatus</a></td>
<td>Most recently observed status of the Deployment.</td>
</tr>
</tbody>
</table>
<h3 id="deploymentspec-v1beta1-1">DeploymentSpec v1beta1</h3>
<table>
<thead>
<tr>
<th>Field</th>
<th>Schema</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>minReadySeconds</td>
<td>integer</td>
<td>Minimum number of seconds for which a newly created pod should be ready without any of its container crashing, for it to be considered available. Defaults to 0 (pod will be considered available as soon as it is ready)</td>
</tr>
<tr>
<td>paused</td>
<td>boolean</td>
<td>Indicates that the deployment is paused and will not be processed by the deployment controller.</td>
</tr>
<tr>
<td>replicas</td>
<td>integer</td>
<td>Number of desired pods. This is a pointer to distinguish between explicit zero and not specified. Defaults to 1.</td>
</tr>
<tr>
<td>revisionHistoryLimit</td>
<td>integer</td>
<td>The number of old ReplicaSets to retain to allow rollback. This is a pointer to distinguish between explicit zero and not specified.</td>
</tr>
<tr>
<td>rollbackTo</td>
<td><a href="#rollbackconfig-v1beta1">RollbackConfig</a></td>
<td>The config this deployment is rolling back to. Will be cleared after rollback is done.</td>
</tr>
<tr>
<td>selector</td>
<td><a href="#labelselector-v1beta1">LabelSelector</a></td>
<td>Label selector for pods. Existing ReplicaSets whose pods are selected by this will be the ones affected by this deployment.</td>
</tr>
<tr>
<td>strategy</td>
<td><a href="#deploymentstrategy-v1beta1">DeploymentStrategy</a></td>
<td>The deployment strategy to use to replace existing pods with new ones.</td>
</tr>
<tr>
<td>template</td>
<td><a href="#podtemplatespec-v1">PodTemplateSpec</a></td>
<td>Template describes the pods that will be created.</td>
</tr>
</tbody>
</table>
<h3 id="deploymentstatus-v1beta1-2">DeploymentStatus v1beta1</h3>
<table>
<thead>
<tr>
<th>Field</th>
<th>Schema</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>availableReplicas</td>
<td>integer</td>
<td>Total number of available pods (ready for at least minReadySeconds) targeted by this deployment.</td>
</tr>
<tr>
<td>observedGeneration</td>
<td>integer</td>
<td>The generation observed by the deployment controller.</td>
</tr>
<tr>
<td>replicas</td>
<td>integer</td>
<td>Total number of non-terminated pods targeted by this deployment (their labels match the selector).</td>
</tr>
<tr>
<td>unavailableReplicas</td>
<td>integer</td>
<td>Total number of unavailable pods targeted by this deployment.</td>
</tr>
<tr>
<td>updatedReplicas</td>
<td>integer</td>
<td>Total number of non-terminated pods targeted by this deployment that have the desired template spec.</td>
</tr>
</tbody>
</table>
<h2 id="write-operations-3">Write Operations</h2>
<p>See supported operations below...</p>
<h2 id="create-4">Create</h2>
<blockquote class="code-block kubectl">
<p> Execute</p>
</blockquote>
<pre class="code-block kubectl"><code class="lang-shell"><span class="hljs-meta">$</span> <span class="hljs-string">echo 'apiVersion: extensions/v1beta1</span>
<span class="hljs-attr">kind</span>: <span class="hljs-string">Deployment</span>
<span class="hljs-attr">metadata</span>:<span class="hljs-string"></span>
  <span class="hljs-attr">name</span>: <span class="hljs-string">deployment-example</span>
<span class="hljs-attr">spec</span>:<span class="hljs-string"></span>
  <span class="hljs-attr">replicas</span>: <span class="hljs-string">3</span>
  <span class="hljs-attr">revisionHistoryLimit</span>: <span class="hljs-string">10</span>
  <span class="hljs-attr">template</span>:<span class="hljs-string"></span>
    <span class="hljs-attr">metadata</span>:<span class="hljs-string"></span>
      <span class="hljs-attr">labels</span>:<span class="hljs-string"></span>
        <span class="hljs-attr">app</span>: <span class="hljs-string">nginx</span>
    <span class="hljs-attr">spec</span>:<span class="hljs-string"></span>
      <span class="hljs-attr">containers</span>:<span class="hljs-string"></span>
      <span class="hljs-meta">-</span> <span class="hljs-string">name: nginx</span>
        <span class="hljs-attr">image</span>: <span class="hljs-string">nginx:1.10</span>
        <span class="hljs-attr">ports</span>:<span class="hljs-string"></span>
        <span class="hljs-meta">-</span> <span class="hljs-string">containerPort: 80</span>
<span class="hljs-meta">'</span> <span class="hljs-string">| kubectl create -f -</span>
</code></pre>
<blockquote class="code-block kubectl">
<p> Returns</p>
</blockquote>
<pre class="code-block kubectl"><code class="lang-shell"><span class="hljs-attribute">deployment</span> <span class="hljs-string">"deployment-example"</span> created
</code></pre>
<p>create a Deployment</p>
<h3 id="http-request-5">HTTP Request</h3>
<p><code>POST /apis/extensions/v1beta1/namespaces/{namespace}/deployments</code></p>
<h3 id="path-parameters-6">Path Parameters</h3>
<table>
<thead>
<tr>
<th>Parameter</th>
<th>Schema</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>namespace</td>
<td></td>
<td>object name and auth scope, such as for teams and projects</td>
</tr>
<tr>
<td>pretty</td>
<td></td>
<td>If &#39;true&#39;, then the output is pretty printed.</td>
</tr>
</tbody>
</table>
<h3 id="query-parameters-7">Query Parameters</h3>
<table>
<thead>
<tr>
<th>Parameter</th>
<th>Schema</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>body</td>
<td><a href="#deployment-v1beta1">Deployment</a></td>
<td></td>
</tr>
</tbody>
</table>
<h3 id="response-8">Response</h3>
<table>
<thead>
<tr>
<th>Code</th>
<th>Schema</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>200</td>
<td><a href="#deployment-v1beta1">Deployment</a></td>
<td>OK</td>
</tr>
</tbody>
</table>
<h2 id="replace-9">Replace</h2>
<blockquote class="code-block kubectl">
<p> Execute</p>
</blockquote>
<pre class="code-block kubectl"><code class="lang-shell">
<span class="hljs-meta">$</span> <span class="hljs-string">echo 'apiVersion: extensions/v1beta1</span>
<span class="hljs-attr">kind</span>: <span class="hljs-string">Deployment</span>
<span class="hljs-attr">metadata</span>:<span class="hljs-string"></span>
  <span class="hljs-attr">name</span>: <span class="hljs-string">deployment-example</span>
<span class="hljs-attr">spec</span>:<span class="hljs-string"></span>
  <span class="hljs-attr">replicas</span>: <span class="hljs-string">3</span>
  <span class="hljs-attr">revisionHistoryLimit</span>: <span class="hljs-string">10</span>
  <span class="hljs-attr">template</span>:<span class="hljs-string"></span>
    <span class="hljs-attr">metadata</span>:<span class="hljs-string"></span>
      <span class="hljs-attr">labels</span>:<span class="hljs-string"></span>
        <span class="hljs-attr">app</span>: <span class="hljs-string">nginx</span>
    <span class="hljs-attr">spec</span>:<span class="hljs-string"></span>
      <span class="hljs-attr">containers</span>:<span class="hljs-string"></span>
      <span class="hljs-meta">-</span> <span class="hljs-string">name: nginx</span>
        <span class="hljs-attr">image</span>: <span class="hljs-string">nginx:1.11</span>
        <span class="hljs-attr">ports</span>:<span class="hljs-string"></span>
        <span class="hljs-meta">-</span> <span class="hljs-string">containerPort: 80</span>
<span class="hljs-meta">'</span> <span class="hljs-string">| kubectl replace -f -</span>

</code></pre>
<blockquote class="code-block kubectl">
<p> Returns</p>
</blockquote>
<pre class="code-block kubectl"><code class="lang-shell">
<span class="hljs-attribute">deployment</span> <span class="hljs-string">"deployment-example"</span> replaced

</code></pre>
<p>replace the specified Deployment</p>
<h3 id="http-request-10">HTTP Request</h3>
<p><code>PUT /apis/extensions/v1beta1/namespaces/{namespace}/deployments/{name}</code></p>
<h3 id="path-parameters-11">Path Parameters</h3>
<table>
<thead>
<tr>
<th>Parameter</th>
<th>Schema</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>name</td>
<td></td>
<td>name of the Deployment</td>
</tr>
<tr>
<td>namespace</td>
<td></td>
<td>object name and auth scope, such as for teams and projects</td>
</tr>
<tr>
<td>pretty</td>
<td></td>
<td>If &#39;true&#39;, then the output is pretty printed.</td>
</tr>
</tbody>
</table>
<h3 id="query-parameters-12">Query Parameters</h3>
<table>
<thead>
<tr>
<th>Parameter</th>
<th>Schema</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>body</td>
<td><a href="#deployment-v1beta1">Deployment</a></td>
<td></td>
</tr>
</tbody>
</table>
<h3 id="response-13">Response</h3>
<table>
<thead>
<tr>
<th>Code</th>
<th>Schema</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>200</td>
<td><a href="#deployment-v1beta1">Deployment</a></td>
<td>OK</td>
</tr>
</tbody>
</table>
</div>
<div id="code-tabs-wrapper" class="code-tabs"><ul class="code-tab-list"><li class="code-tab" id="kubectl">kubectl</li></ul></div>
</div>
<script src="https://code.jquery.com/jquery-3.1.1.min.js" integrity="sha256-hVVnYaiADRTO2PzUGmuLJr8BLUSjGIZsDYGmIJLv2b8=" crossorigin="anonymous"></script>
<script src="actions.js"></script>
<script src="tabvisibility.js"></script>
</body>
</html>
