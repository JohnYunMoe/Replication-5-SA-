# Notes

Some weird things
- They use env var for the Github token, which is good, but then don't use for other configuration settings like SonarQube's token and url (which instead, is redefined in several cells, so harder to change)
- result_analysis.ipynb
	- If LOC info isn't in the dataset, it will literally generate random numbers with np.random.randint! This is nonsense! Luckily the dataset has it, so it won't.
	- Manually uncommented some lines, such as saving latex table Hierarchical_Issue_Type_Severity_Agent_Table
	- Fixed errors
		- Why are there 3 different filenames for the same csv file, and none of them are correct?
			- pd.read_csv('5.All_PR_Sonar_Results.csv')
			- pd.read_csv('6.All_PR_Sonar_Results.csv')
			- pd.read_csv('All_PR_Sonar_Results.csv')
			- It should be, '../dataset/All...'
			- Update: It's for other files too, not just this one. (.json, etc)
		- `for issue_type in issue_types:` -> `for issue_type in df["Issue Type"].unique():`
- So many dependencies not mentioned in their README
	- README says: `pip install pandas numpy matplotlib seaborn requests python-dotenv`
	- Missing deps: `pip install scipy scikit_posthocs cliffs_delta pandas[pyarrow] fsspec huggingface_hub`

- Btw, author has her GitHub and OpenAI tokens, as well as the other authors's GitHub tokens in the repo. She deleted the .env file, but that doesn't remove it from Git's history