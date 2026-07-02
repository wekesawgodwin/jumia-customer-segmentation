# Customer Segmentation using Machine Learning

## Project Title

Customer Segmentation using Machine Learning for Jumia

## Overview

This repository presents a professional capstone project that applies customer segmentation techniques to support business decision-making in an e-commerce context. The project is framed as a consulting-style analytical engagement for Jumia and follows the CRISP-DM methodology.

The objective is to transform transaction data into meaningful customer segments that can help the business identify valuable customers, detect at-risk customers, and improve marketing strategy. The work combines business analysis, machine learning, and clear documentation in a format suitable for academic submission and GitHub publication.

## Business Problem

In a competitive digital retail environment, businesses must understand customer behavior in order to allocate resources effectively and build lasting customer relationships. Jumia, like many e-commerce companies, faces the challenge of managing a large and diverse customer base with different purchasing behaviors.

Some customers are highly valuable and purchase regularly, while others may be occasional buyers or at risk of disengagement. Without a structured segmentation approach, it becomes difficult to target campaigns efficiently, retain customers, and maximize revenue.

This project addresses that challenge by using machine learning to uncover customer segments based on historical transaction behavior.

## Objectives

The key objectives of this project are to:

- translate the project brief into a formal business problem,
- define customer value and customer risk,
- apply RFM analysis to understand purchasing patterns,
- use clustering to discover customer segments,
- and present actionable insights for business use.

## Dataset

This project uses the Online Retail Dataset (UCI), which contains transactional retail data suitable for customer behavior analysis. Although the dataset is not from Jumia directly, it provides a realistic foundation for demonstrating customer segmentation techniques that are directly relevant to e-commerce strategy.

## Repository Structure

- [01_business_understanding.md](01_business_understanding.md) — business analysis and problem framing
- [02_project_charter.md](02_project_charter.md) — project scope, goals, timeline, and responsibilities
- [03_weekly_progress_tracker.md](03_weekly_progress_tracker.md) — sprint planning and weekly progress tracking
- [Netflix_Movie_Recommendation_System.ipynb](Netflix_Movie_Recommendation_System.ipynb) — existing notebook workspace file

## CRISP-DM

This project follows the CRISP-DM lifecycle:

1. Business Understanding
2. Data Understanding
3. Data Preparation
4. Modeling
5. Evaluation
6. Deployment Thinking

## Installation

To work with the project locally, install the required Python packages:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

## Requirements

The project uses the following tools and libraries:

- Python 3.8+
- pandas
- NumPy
- matplotlib
- seaborn
- scikit-learn

## Workflow

The workflow for this project is as follows:

1. Understand the business problem and define objectives.
2. Explore and prepare the dataset.
3. Create customer-level RFM features.
4. Apply clustering techniques to discover segments.
5. Interpret the results and translate them into business recommendations.

## Results

The expected outcome of this project is a practical customer segmentation framework that helps identify:

- high-value customers,
- frequent buyers,
- occasional buyers,
- and customers who may require retention efforts.

## Future Work

Future enhancements could include:

- applying more advanced clustering methods,
- integrating real-world customer transaction data,
- building a dashboard for segment monitoring,
- and linking segmentation outcomes to marketing automation.

## Contributors

- Trevor — Project Lead, Business Analyst, Scrum Master, and Technical Writer

## License

This project is intended for academic and educational purposes.

## Acknowledgements

Special thanks to the UCI Machine Learning Repository for providing the Online Retail Dataset and to the open-source Python community for the tools used in this analysis.
