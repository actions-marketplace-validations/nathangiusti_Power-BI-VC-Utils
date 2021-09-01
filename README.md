# Power-BI-VC-Utils

GitHub Action for pretty printing Power BI Dataflow JSON and PBIX report JSON. 

Takes in a list of files. 

For all .json (dataflow) files, pretty prints 

For all .pbix report files deserializes and pretty prints report json.

Tales as input files, a space delineated list of json and PBIX files to iterate over. 

Example use:
	
~~~~
name: Reformat Power BI Assets
on: [pull_request]
jobs:
  Reformat-Power-BI-Assets:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
        with:
          ref: ${{ github.head_ref }}
      - id: files
        uses: jitterbit/get-changed-files@v1
      - name: Power BI VC Utils
        uses: nathangiusti/Power-BI-VC-Utils@v1.0
        with:
          files: ${{ steps.files.outputs.all }}
      - uses: stefanzweifel/git-auto-commit-action@v4
        with:
          commit_message: Reformatted files for VC
~~~~

NOTE:

In order for this action to work you must copy run.py into .github/scripts

If anyone knows how to get docker to run the python script in the action, please reach out. 
