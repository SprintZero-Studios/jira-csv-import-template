# Jira CSV import template

A CSV template for importing epics and linked stories into Jira, with the
columns Jira's CSV importer maps and the import steps. Have a PRD already?
The free converter at trymurmur.studio writes this CSV from it in your browser.

- `epics-and-stories.csv`: Jira Cloud. Replace the sample rows with yours.
- `epics-and-stories-data-center.csv`: the same rows for Jira Data Center.
- `examples/awas-jira-cloud.csv`: a real board, the 17 epics and
  64 stories from a Murmur run (Awas), published with the owner's permission.

Use it: click "Use this template", or download epics-and-stories.csv.

## The columns (Jira Cloud)

Header names match Jira's field names, so every column maps one-to-one.
Parents always come before their children.

| Column | What goes in it |
| --- | --- |
| `Work item ID` | A unique number per row: epics 1…n, then stories |
| `Work type` | Epic, then Story (or Task) |
| `Summary` | The epic or story title, up to 255 characters |
| `Description` | Optional. Plain text; line breaks are kept inside quotes |
| `Parent` | On stories: the epic's Work item ID. Blank on epics |
| `Priority` | Optional. High, Medium, Low or Lowest from MoSCoW |
| `Labels` | Optional. One column per label, e.g. must-have |

## Jira Data Center

`epics-and-stories-data-center.csv` uses the older epic fields:

| Column | What goes in it |
| --- | --- |
| Issue Type | Epic, then Story (or Task) |
| Summary | The epic or story title |
| Epic Name | On epics: a unique name |
| Epic Link | On stories: the Epic Name of its epic |
| Description, Priority, Labels | Same as the Cloud file |

## How to import it into Jira Cloud

Linking stories to epics needs Jira's admin CSV importer (External System
Import).

1. Go to **Settings** (the cog) → **System**. Under **Import and Export**, select **External System Import**, then **CSV**. If Jira offers the new import experience, select **switch to the old experience**.
2. Choose your CSV file. Leave **Use an existing configuration file** unticked; the defaults under **Advanced** (UTF-8, comma delimiter) are right. Select **Next**.
3. Under **Select a space**, pick the space the epics should land in, then select **Next**.
4. Map each column to the Jira field of the same name: `Work item ID`, `Work type`, `Summary`, `Description`, `Parent`, and `Priority` / `Labels` if present. Summary is required. Select **Next**.
5. On the value-mapping screen, leave values as they are (or map `Story` to `Task` if your space has no Story type), then select **Begin Import**.

**Starting a new space instead?** Admins can select **Create space** in the sidebar, then **Import data** → **CSV**. On the mapping screen, map the columns to **work item ID**, **parent** and **work type** to keep the hierarchy.

**Not a Jira admin?** **Filters** → **Search work items** → **•••** → **Import work items from CSV** imports up to 250 items, but Atlassian says it can't map parent-child links. Stories arrive unlinked, so ask an admin to run the import.

**Jira Data Center:** use `epics-and-stories-data-center.csv`, then go to **Administration** → **System** → **External System Import** → **CSV** and map `Issue Type`, `Summary`, `Epic Name`, `Epic Link` and `Description`. If stories fail to link, split the file: import the epic rows first, then the story rows.

Sources (Atlassian Support, checked September 2026):

- [Import data from a CSV file](https://support.atlassian.com/jira-cloud-administration/docs/import-data-from-a-csv-file/)
- [Keep parent-child relationships during CSV import](https://support.atlassian.com/jira/kb/keep-issue-parent-child-mapping-during-csv-import-to-jira-cloud/)
- [Import data to Jira using a CSV file](https://support.atlassian.com/jira-software-cloud/docs/import-data-to-a-software-project-using-a-csv-file/)
- [Create work items using the CSV importer](https://support.atlassian.com/jira-software-cloud/docs/create-issues-using-the-csv-importer/)
- [Fix Epic Link CSV import errors (Data Center)](https://support.atlassian.com/jira/kb/fix-epic-link-csv-import-format-errors-jira/)

Want it written for you? Murmur by SprintZero Studios turns a spoken idea
into a PRD, research, brand kit, tech design and a roadmap along with the
entire task breakdown. First idea free:
https://app.trymurmur.studio/?utm_source=github&utm_medium=template&utm_campaign=jira-csv-import-template

More: https://www.trymurmur.studio/tools/prd-to-jira-csv

License: CC BY 4.0, SprintZero Studios. Reuse it with credit, for example:
"Based on the Jira CSV import template by SprintZero Studios (https://www.trymurmur.studio/tools/prd-to-jira-csv), CC BY 4.0."
