# approval_task

STEP 1 : **Your need to change your route URL inside frontend_cm :**
---------------------------EXAMPLE---------------------------
.............</head>
    <body>
      <h1>Approval Task</h1>
        <div class="container">
            <div class="row">
                <div class="col">
                </div>
                <div class="col">
                    <form method="POST" action="**http://approval-test.apps.cluster-vsrjf.vsrjf.sandbox2991.opentlc.com**/submit">
                            <button type="submit" name="approval" value="true">Approve</button>
                            <button type="submit" name="approval" value="false">Reject</button>
                    </form>.........................
   
                  
                  
                  
                  
STEP 2 : Add this value in pipeline where you add your approval task : **- name: $(context.pipelineRun.name)**....so that it can able fetch PipelineRun name
-------------------EXAMPLE------------------------------
                  apiVersion: tekton.dev/v1beta1
kind: Pipeline
metadata:
  name: tekton-ci
  namespace: sumit
spec:
  params:
    - default: 'https://github.com/sumitbiswal98/pipeline_tasks_yaml.git'
      description: The GitHub Repo of the Java Application
      name: GITHUB_REPO_URL
      type: string
    - default: main
      description: The GitHub revision to use
      name: GITHUB_REPO_REVISION
      type: string
  tasks:
    - name: final-approval-task
      params:
        - name: form-link
          value: >-
            http://approval-sumit.apps.cluster-vsrjf.vsrjf.sandbox2991.opentlc.com/
        - name: server
          value: server-secret
        - name: sender
          value: imssdevops99@gmail.com
        - name: recipients
          value: sumitbiswal98@gmail.com
        **- name: pipeline
          value: $(context.pipelineRun.name)**
      runAfter:
        - git-clone
      taskRef:
        kind: Task
        name: final-approval-task
  workspaces:
    - name: approval

                  
                  
                  
