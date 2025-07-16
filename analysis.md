# Credit Score Analysis for Aave V2 Wallets

This file explains what was done in this project, how the credit scores were calculated, and what the results say about different wallet behaviors on the Aave V2 platform. Everything here is focused on the actual steps and results from the project, in simple words.

---

## What Was the Goal?

The goal of this project was to give each wallet that used Aave V2 a credit score. This score is a number between 0 and 1000 and shows how safely and responsibly each wallet used Aave’s features like borrowing, lending, and repaying.

---

## How Did the Project Work?

1. **Collected Data:**  
   Took raw data about what each wallet did on Aave V2 (like deposits, borrows, repayments, and liquidations).

2. **Calculated Features:**  
   For each wallet, worked out the following:
   - **deposit_count:** How many times the wallet put money into Aave.
   - **borrow_count:** How many times it took a loan.
   - **repay_count:** How often it paid loans back.
   - **liquidation_count:** How often the wallet lost its deposit due to not repaying.
   - **repay_ratio:** How many loans were fully repaid, as a ratio.
   - **unique_actions:** Number of different things the wallet did on Aave.
   - **days_active:** How many days the wallet used Aave.
   - **transactions_per_day:** How busy the wallet was on days it was active.
   - **liquidation_rate:** How often the wallet was liquidated after borrowing.

3. **Assigned Credit Scores:**  
   Used a rule-based formula where good actions (like repaying) added to the score, and bad actions (like being liquidated) dropped the score. The formula mixed all the features together and gave each wallet a score from 0 (very risky) to 1000 (very safe).

4. **Labeled Wallets:**  
   Based on their score, each wallet got a label:
   - Excellent (800–1000)
   - Good (600–800)
   - Fair (400–600)
   - Poor (200–400)
   - Very Poor (0–200)

5. **Saved the Results:**  
   Made a CSV file with all the wallet scores and labels for easy checking later.
    The complete code for all these steps is in `zeru.ipynb`.
---

## What Do the Results Show?

### Score Distribution

Most wallets had scores in the middle or low range. Fewer wallets scored at the very top.  
*A score distribution chart was created and added to show this visually in score_distribution.png*

- **Wallets with High Scores (Excellent/Good):**
  - Almost always repay their loans.
  - Rarely get liquidated.
  - Stay active on Aave for a long time.
  - Use multiple features on Aave, not just one thing.
  - Generally safe, careful, and reliable users.

- **Wallets with Low Scores (Poor/Very Poor):**
  - Get liquidated often (lose deposits because loans weren’t repaid).
  - Rarely or never repay what they borrow.
  - Usually only use Aave for a short time, or do just one type of action.
  - Risky — these users cost the protocol more and are less trustworthy.

- **Wallets with Fair Scores:**
  - Do a mix of good and bad actions.
  - May have some liquidations or missed repayments but also show some responsible behavior.


---

## What Did I Learn From the Data?

1. The scoring rules make it easy to see which wallets are safe and which ones are risky.

2. Most wallets with “Excellent” scores used Aave for a long time, tried out many features, and almost always paid back what they borrowed.

3. Most wallets with “Very Poor” scores lost their deposits often and usually left soon after.

4. Looking at things like how often people repay and how often they get liquidated is a good way to tell who is reliable and who is not.

---

## Conclusion

By looking at simple on-chain actions, this project was able to sort Aave V2 wallets by risk. The process and scoring are easy to follow, and the results can help identify which users are safest and which ones should be watched closely or avoided. The project proves that clear rules and careful feature selection can give useful credit scores, even in a decentralized system with no traditional credit history.

