# Description

This project was completed as part of an internship assignment.  This project builds an explainable "credit scoring" model for Aave V2 protocol users, using only on-chain transaction data. Each wallet is scored (0–1000),By analyzing user on-chain actions—such as deposits, borrows, repayments, and liquidations—the system quantifies wallet reliability.This project creates a **credit score** for users (wallets) on the Aave V2 platform based on how they use the lending and borrowing features. It helps identify which users are trustworthy and which ones might be risky or careless.

## Method Chosen

I used a **rule-based scoring method**. For each wallet, we looked at its borrowing, repaying, depositing, and liquidation activity. We designed features that measure how often and how responsibly each wallet behaved, then combined these features using a scoring formula to get a final credit score between 0 and 1000.


## Architecture and Processing Flow

1. **Data Loading**
   - The code reads raw wallet transaction records from Aave V2.

2. **Feature Extraction**
   - For each wallet, we calculate several features:
     - **deposit_count:** How many times the wallet deposited assets into Aave.
     - **borrow_count:** How many times the wallet borrowed assets.
     - **repay_count:** How many times the wallet repaid borrowed assets.
     - **liquidation_count:** How many times the wallet was liquidated (lost collateral).
     - **repay_ratio:** Portion of borrows that were eventually repaid.
     - **unique_actions:** Number of different activity types the wallet performed.
     - **days_active:** How long the wallet has been using Aave, from first to last transaction.
     - **transactions_per_day:** Average number of actions per active day.
     - **liquidation_rate:** Ratio of liquidations to total borrows—shows riskiness.
   
3. **Score Calculation**
   - We use a formula to combine the features, giving higher scores to wallets that repay, use Aave for longer, and perform more types of actions, and lower scores to wallets with many liquidations or unrepaid loans.

4. **Label Assignment**
   - Based on the credit score, each wallet is labeled as Excellent, Good, Fair, Poor, or Very Poor.

5. **Output**
   - All results (wallet, score, label) are saved to a CSV file for review and further analysis.

## Technologies Used

- Python with Jupyter Notebook for code
- pandas and numpy for data handling
- matplotlib for graphs
- Git and GitHub for version control and sharing code


## How to run
### To Run

1. Open `zeru.ipynb`.
2. Run all cells to see wallet scores.
3. See `credit_scores.csv` for results.
4. Find more analysis in `analysis.md`.


# Contributing

Contributions are always welcome!

If you'd like to contribute to this project, feel free to open an issue or submit a pull request. Contributions are welcome!

🤝 Contributing
We welcome contributions to improve SmartBot! Here's how you can help:
Ways to Contribute

- Bug Reports: Report issues or bugs you encounter
- Feature Requests: Suggest new features or improvements
- Code Contributions: Submit pull requests with enhancements
- Documentation: Help improve documentation and examples
- Testing: Test the bot on different systems and scenarios

Getting Started

Fork the repository
Create a feature branch
```bash
bashgit checkout -b feature/your-feature-name
```
Make your changes
Test thoroughly
Submit a pull request

Contribution Guidelines

Follow Python PEP 8 style guidelines,
Add comments for complex logic,
Update documentation for new features,
Test your changes before submitting,
Ensure compatibility with existing functionality.

Areas for Improvement

Cross-platform compatibility (Linux/Mac support),
Additional voice engines (Amazon Polly, Google TTS),
More intent categories (weather, news, calculations),
Database integration for conversation history,
GUI interface for better user experience,
Multi-language support,
Voice training capabilities.
