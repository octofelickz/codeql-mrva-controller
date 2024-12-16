# codeql-mrva-controller

See [run results](./runs.md)


# MRVA?

https://github.blog/security/vulnerability-research/multi-repository-variant-analysis-a-powerful-new-way-to-perform-security-research-across-github/


The security community identifies new vulnerabilities at an astonishing rate and helps developers all over the world secure their code. GitHub is actively facilitating this collaboration with tools like private vulnerability reporting and the GitHub Advisory Database. Today, we’re announcing the next big step in our mission to help the community secure the world’s code: multi-repository variant analysis (MRVA).

Variant analysis is an important technique for identifying new types of security vulnerabilities. CodeQL, the static analysis engine that powers code scanning, is a great tool for variant analysis because it allows you to model vulnerabilities as highly precise custom CodeQL queries. The use of queries offers a deep level of customization, allowing security researchers the flexibility to find exactly what they’re looking for. MRVA scales this deep analysis capability: with many thousands of repositories at your fingertips, it’s now easy to scale variant analysis across large numbers of codebases, saving time and allowing you to rapidly hunt for new vulnerabilities.

GitHub’s own Security Lab has already been leveraging multi-repository variant analysis to detect new vulnerabilities, including recent Android advisories that affected over 10 million applications. For a full list of the vulnerabilities our Security Lab uncovered, check out the advisories page.

## How does variant analysis work with CodeQL?

When you run a CodeQL query against a codebase, not only will it identify the original problem you modeled, but it can also pick up logical variants of the problem, helping to identify entire classes of vulnerabilities in one go. This technique can be useful in identifying and analyzing new vulnerabilities, especially those that are based on previously known vulnerabilities or attack patterns.

In the context of MRVA, if an exploit is suspected to be based on a known vulnerability in a specific software package, community researchers can analyze entire codebases and compare their code to known variants of the exploit. By identifying similarities and differences between the two, they can gain insights into how the exploit works, and what steps can be taken to prevent or mitigate the attack.

## How to get started using multi-repository variant analysis
Running a CodeQL query with MRVA is very similar to running a query against a single codebase in CodeQL for Visual Studio Code (VS Code). Queries are run against CodeQL databases, which are representations of a codebase containing queryable information about the code’s syntactic structure, dataflow graph, and control flow graph.

MRVA allows you to run your CodeQL query against a list of up to 1,000 repositories. Rather than downloading the CodeQL databases for each repository into VS Code, MRVA triggers a GitHub Action that obtains all the CodeQL databases and executes your query against each one. As each query completes, the results are sent back to VS Code for you to explore.

![image](https://github.com/user-attachments/assets/42974247-14b3-4a8e-ad6b-47c4547107ca)


multi repository variant analysis results display in VS Code

MRVA automatically creates lists of 10, 100, and 1,000 public repositories for you to easily test your CodeQL queries against. These lists were developed in partnership with GitHub’s code search team and feature a range of OSS repositories for each language supported by CodeQL. If you’d prefer to target different repositories, we also support the creation of custom lists or you can even trigger an MRVA run against up to 1,000 repositories in a single GitHub organization.

Once your results are in, you can find the alerts you care about the most by sorting the repositories by their star counts or the time they were last updated. If you find a result that you want to share with a colleague or a project maintainer then you can easily generate lightweight Markdown reports using our “Export results” feature.

## Which repositories are available for multi-repository variant analysis?
For public repositories, we store CodeQL databases for every repository that runs GitHub code scanning. That means if you want your public repository to be available for MRVA, then simply enable code scanning with CodeQL.

However, we also want to give you the flexibility to run variant analysis on repositories that may not be running code scanning with CodeQL. To this end, we store CodeQL databases for thousands of public repos on GitHub.com that don’t have code scanning enabled. We’ve made these repositories available for MRVA so that the CodeQL community can help keep open source software secure—like code search on steroids! The list of repositories available for MRVA is ever-evolving to make sure that the most relevant repositories are available for security research with CodeQL.

You can also use MRVA to analyze any private repositories that you have read access to, as long as code scanning with CodeQL is enabled. So, when you’ve developed a CodeQL query to detect a new vulnerability, you can also use MRVA to identify and eliminate bugs in your organization’s entire portfolio.

For more information on how to set up and leverage multi-repository variant analysis, please refer to our documentation.
