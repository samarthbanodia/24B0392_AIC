# 1 month AI Hackathon Prep Timeline

## Week 1: Ideation and POA Planning

* Go through available problem statements in the hackathon and select one that interests or seems unique.
* lets take example of a PS from SIH 2024: **AI-Powered Student Assistance Chatbot for Department of Technical Education, Government of Rajasthan**

* **Quantitative Formulation:** Define the problem in measurable terms:

  * 24/7 online, <2 seconds average response time ,90% accuracy on FAQ responses during internal testing
* **Feasibility Check:**

  * Explore Kaggle, Huggingface, and other platforms for suitable datasets
  * Check availability of departmental data for model training
* **Plan of Action (POA):**

  * Create a poa with tech stack, suggested tools, divide work 
  * Consult with professionals and mentors for feedback adn advice

## Week 2: Sourcing Data and Preprocessing

* Search for relevant datasets (Kaggle, Huggingface, UCI, official websites)
* Scrape data from:

  * Department of Technical Education Rajasthan website
  * Official reports, articles, and documents
* in our example gather structured information:

* Admission rules,
   Fee structures,
   College profiles,
   Course details,
   Scholarships,
   Hostel information etc
* Clean and standardize data
* Categorize and format data for database integration

## Week 3: Exploratory Data Analysis (EDA)

* Perform EDA:

  * Calculate mean, mode, median, standard deviation
* Use visual tools:

  * Matplotlib, Seaborn for distribution and correlation plots
* Document insights:

  * Prepare visually appealing charts for presentation

## Week 4: Model Selection, Training Strategies, Compute Requirements

* **Model Selection:**

  * Choose based on data complexity (eg BERT, GPT-4, Rag with LLM etc)

* **Training Strategy:**

  * Establish baseline performance expectation.
  * Tune hyperparameters.
  * Use validation sets.
  * Consider transfer learning or other methods.

* **Compute Requirements:**

  * Evaluate CPU/GPU needs
  * Calculate token usage costs for LLM APIs
  * Assess hosting cost (AWS, Huggingface spaces etc)

* **Evaluation Metrics:**

  * Define appropriate metrics to track PS success

## Team Roles

1. **Team Leader/Project Manager:**

   * Coordinates workflow
   * Sets milestones
   * Oversees documentation and presentation
   * Handles app hosting

2. **Data Scientist:**

   * Data exploration, cleaning, preprocessing
   * Extracts data from reports and websites
   * in SIH eg: Helps develop NLP model

3. **ML Engineer:**

   * Optimizes ML pipeline
   * Hyperparameter tuning
   * in our eg : Implements vector database and LLM APIs

4. **Frontend & Backend Developer:**

   * Designs UI (Streamlit, Bolt etc or from scratch)
   * Integrates backend APIs and database
   * Hosts app online

5. **UX and Presentation Lead:**

   * Crafts user experience
   * Prepares pitch and demo video

## Milestones

* **End of Week 1:**

  * Clear POA with functionality and tech stack
  * Identified data sources

* **End of Week 2:**

  * Data collection and preprocessing complete
  * EDA insights and correlations documented 

* **End of Week 3:**

  * MVP model with expected performance ready
  * Frontend ready

* **End of Week 4:**

  * Final model testing complete
  * Presentation and demo prepared

## Risk Mitigation Strategies

* **Model underperformance:**

  * Try simpler ML models or methods 
  * Use different datasets or data processing methods

* **Technical issues:**

  * Schedule regular team meetings for debugging
  * Let everyone see each others problem

* **Poor data availability/quality:**

  * Find backups for datasets
  * Generate synthetic data using llms

* **User adoption issues:**

  * Conduct early testing
  * Gather user feedback
