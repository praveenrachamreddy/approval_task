# approval_task

STEP 1 : **You need to change your route URL inside frontend_cm : action attribute----->**
---------------------------EXAMPLE---------------------------
.............</head>
    <body>
      <h1>Approval Task</h1>
        <div class="container">
            <div class="row">
                <div class="col">
                </div>
                <div class="col">
                    <form method="POST" action="---http://approval-test.apps.cluster-vsrjf.vhtrjf.sandbox2991.opentlc.com----/submit">       <<<-------
                            <button type="submit" name="approval" value="true">Approve</button>
                            <button type="submit" name="approval" value="false">Reject</button>
                    </form>.........................
