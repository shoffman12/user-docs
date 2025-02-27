# Manage code vulnerabilities

## Prerequisites for managing code vulnerabilities in Snyk Web UI&#x20;

Before managing vulnerabilities with Snyk Code, ensure the following:

* You have completed [Quickstart](../../../getting-started/quickstart/).
* Your repositories contain code in a [supported language and platform](../../../getting-started/supported-languages-and-frameworks/).&#x20;
* You have [configured Snyk Code](../configure-snyk-code.md).

## How Project testing works for Snyk Code

Each time a Project is tested, Snyk Code takes a snapshot of the repository in its current state and analyzes it to find vulnerabilities.  All the files that contain source code that Snyk Code can analyze are aggregated in the Code analysis.

When you import a repository, Snyk creates a Target folder that contains different Snyk Projects based on the file types present in the repository. The name of the Target folder includes the repository name, the integrated Git repository account name and its icon, and the number of Snyk Projects created for the repository. See [View your first Snyk Projects](../../../implement-snyk/walkthrough-code-repository-projects/view-your-first-snyk-projects.md).

Snyk Code creates a single Project for all the imported files from a repository. This aggregates vulnerabilities detected in the repository code into one Project, presenting the data flow of a vulnerability issue across multiple files.

## Code testing from import to retest

Here is an overview of the testing process in Snyk Code based on the testing phases.

<table><thead><tr><th width="250">Phase</th><th>Description</th></tr></thead><tbody><tr><td><a href="../import-repository-to-snyk/">Import repository</a></td><td>Performed when you import a repository.</td></tr><tr><td><a href="../../../snyk-admin/snyk-projects/view-and-edit-project-settings.md">Schedule recurring tests</a></td><td>Automatically performed when you schedule them.</td></tr><tr><td><a href="./#retesting-code-repository">On demand testing (retesting code repository)</a></td><td>Performed on demand when you select <strong>Retest now</strong>.</td></tr></tbody></table>

### Retesting code repository

If you want to check for the most recent vulnerabilities in your repository, you can do a manual test by clicking the **Retest now** option. This will trigger Snyk Code to take a fresh snapshot of your repository and analyze its source code files. The results will then be displayed on the Code Analysis page. Take into consideration that Snyk counts a manual test as a new test. See [What counts as a test?](../../scanning-overview/what-counts-as-a-test.md)

You can also use the **Retest now** option to apply the exclusion rules of the `.snyk` file to an imported repository. See [Excluding directories and files from the import process](../import-repository-to-snyk/excluding-directories-and-files-from-the-import-process.md).

<figure><img src="../../../.gitbook/assets/Retest Code.png" alt="Retesting a repository."><figcaption><p>Retesting repository </p></figcaption></figure>

## Project filters

The Projects page on Snyk Web UI has a filter pane that categorizes Snyk Projects and shows the number of matching Projects for each criterion. See [Project information](../../../snyk-admin/snyk-projects/view-project-information.md).

## Vulnerability issues

You can change the display of the issues on the Code analysis page using the following options:

* Grouping by **File** or **Vulnerability Type** to identify problematic files with multiple issues or address prevalent vulnerability types.
* Sorting from the **Highest** or the **Lowest** severity level.
* Filtering discovered vulnerability issues according to different criteria shown in the following table.&#x20;

<table><thead><tr><th width="232">Vulnerability issue filter</th><th>Description</th></tr></thead><tbody><tr><td><a href="../../../manage-risk/prioritize-your-issues/severity-levels.md">Severity level</a></td><td>Show issues with a certain severity level. Snyk Code uses only <strong>High</strong>, <strong>Medium</strong>, and <strong>Low</strong> severity levels, without <strong>Critical</strong>. </td></tr><tr><td><a href="../../find-and-manage-priority-issues/priority-score.md#calculation-of-priority-score">Priority score</a></td><td>Show issues in a certain priority score range.</td></tr><tr><td>Status</td><td>Show <strong>Open</strong> issues or issues that were <strong>Ignored</strong>.</td></tr><tr><td><a href="../../../getting-started/supported-languages-and-frameworks/">Languages</a></td><td>Show issues that were discovered in code files that were written in a specific language. Only programming languages discovered in the analyzed repository are displayed in the Filter pane.</td></tr><tr><td><a href="../snyk-code-security-rules/">Vulnerability types</a></td><td>Show issues with a certain Vulnerability Type. See <a href="../snyk-code-security-rules/">Snyk Code security rules</a>.</td></tr></tbody></table>

<figure><img src="../../../.gitbook/assets/Vulnerability issues.png" alt="Overview of vulnerability issue filtering, sorting, and grouping."><figcaption><p>Vulnerability issue filtering, sorting, and grouping</p></figcaption></figure>

## **Scan for code vulnerabilities**

To scan your repositories and manage code vulnerabilities, you can check the following actions.

### View vulnerabilities in a repository

1. Log in to the Snyk Web UI and select your [Group and Organization](../../../snyk-admin/groups-and-organizations/).
2. Navigate to the **Projects** and select the Target folder containing your repository's Projects.
3. Open **Code analysis** Project to see all vulnerability issues detected by Snyk Code.

To understand the results, see [Breakdown of Code analysis](breakdown-of-code-analysis.md).&#x20;

### Import additional repositories

If you have existing Projects in your Snyk account, you can add additional repositories for Snyk to test. See [Import repository to Snyk](../import-repository-to-snyk/#import-repository-to-snyk).

### Remove repositories from testing

You can remove the Code analysis Project or delete imported repositories if you no longer need to test them for vulnerabilities. See [Remove imported repository](../import-repository-to-snyk/remove-imported-repository.md).

### Exclude directories and files

Adjust your import settings to exclude specific directories and files from being tested.

To exclude specific files and directories from being imported by Snyk Code, you need to create a `.snyk` YAML policy file in your repository. See [Exclude directories and files from the import process](./#exclude-directories-and-files).

### Open repository external link&#x20;

To access the repository on the integrated Git repository platform, navigate to the Code analysis Project and select the name of the repository.

<figure><img src="../../../.gitbook/assets/Open repository external link.png" alt="Overview of the external repository link."><figcaption><p>External repository link</p></figcaption></figure>

### View Project history

The result history is shown on the **History** page of the **Code Analysis** Project. This page displays the snapshots taken when a test was performed. You can review Snyk Code test results for all the testing phases. See [Code testing from import to retest](./#code-testing-from-import-to-retest).

On the **History** page, only two distinct snapshots are displayed. A snapshot is deemed unique if either the repository or its associated vulnerability findings have altered since the last assessment, resulting in a snapshot that showcases these changes. If there have been no changes in the repository or the vulnerability results since the last test, the new snapshot will replicate the prior one. Consequently, this will be listed as an additional test run on the **History** page. This means while the page may present multiple test entries, only up to two will feature distinct results.

To view Project history:

1. Log in to the Snyk Web UI and select your [Group and Organization](../../../snyk-admin/groups-and-organizations/).
2. Navigate to the **Projects** and select the Target folder containing your repository's Projects.
3. Open **Code analysis** Project and navigate to **History**.
4. Select a test from the list to view the Project historical snapshot.
5. (Optional) Select **View most recent snapshot**. This option is not available when the most recent snapshot is open.

<figure><img src="../../../.gitbook/assets/Project history.png" alt="Overview of Snyk Code Project history"><figcaption><p>Snyk Code Project history</p></figcaption></figure>

### Manage Project settings

Manage Project settings as follows:

* Schedule recurring tests: [Configure Test & Automated Pull Request Frequency](../../../snyk-admin/snyk-projects/#test-frequency-settings).
* Retrieve the Project ID: [Retrieve the unique identifier for the Project](../../../snyk-admin/snyk-projects/#project).
* Deactivate Project: [Temporarily disable the Project without deleting any data](../../../snyk-admin/snyk-projects/#delete-activate-or-deactivate).
* Delete the Project: [Permanently remove the Project and all associated data](../../../snyk-admin/snyk-projects/#delete-activate-or-deactivate).

## What's next?

* [See the breakdown of Code analysis](breakdown-of-code-analysis.md)
* [Fix code vulnerabilities automatically](fix-code-vulnerabilities-automatically.md)
* [See Snyk Code security rules](../snyk-code-security-rules/)
