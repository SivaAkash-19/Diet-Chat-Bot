# Diet Knowledge Graph

This project builds a NetworkX-based knowledge graph connecting nutritional ingredients, food items, patient conditions, and dietary recommendations for personalized nutrition advice.

## Files Created

1. `build_diet_knowledge_graph.py` - Basic food-ingredient-nutrient graph
2. `build_enhanced_diet_kg.py` - Enhanced graph with patient condition connections
3. `query_diet_kg.py` - Demo queries for basic graph
4. `query_enhanced_diet_kg.py` - Demo queries for enhanced graph
5. `diet_knowledge_graph.gpickle` - Saved basic knowledge graph
6. `enhanced_diet_knowledge_graph.gpickle` - Saved enhanced knowledge graph
7. `graph_summary.json` - Summary of basic graph
8. `enhanced_graph_summary.json` - Summary of enhanced graph

## Graph Structure

### Nodes
- **Food Items**: Prepared dishes with nutritional info and dietary tags
- **Ingredients**: Raw food components with detailed nutritional profiles
- **Chronic Diseases**: Medical conditions like Diabetes, Hypertension, etc.
- **Meal Plans**: Recommended dietary approaches (Low-Fat, High-Protein, etc.)
- **Allergies**: Common food allergies (Lactose Intolerance, Nut Allergy, etc.)

### Edges
- **contains**: Food → Ingredient (what ingredients make up a food)
- **recommends**: Condition → Meal Plan (what diet is suggested for a condition)
- **has nutrient**: Implied through ingredient nutritional data

## Usage

### Loading the Graph
```python
import pickle
import networkx as nx

# Load enhanced graph
with open('enhanced_diet_knowledge_graph.gpickle', 'rb') as f:
    G = pickle.load(f)
```

### Example Queries
See `query_enhanced_diet_kg.py` for detailed examples, including:
- Getting recommended meal plans for medical conditions
- Finding suitable foods for specific dietary plans
- Identifying ingredients to avoid for allergies
- Retrieving nutritional information for ingredients and foods

## Dataset Sources
- `nutrition_data_my.csv`: Nutritional profiles of 237 Sri Lankan ingredients
- `Illness__Diet_Recommendations.csv`: 5000 patient records with conditions and diet recommendations
- `food_ingredient_my.csv`: 200 prepared Sri Lankan food items with their ingredients

## Graph Statistics
- Enhanced graph: 559 nodes, 627 edges
- Node types: food, ingredient, chronic_disease, meal_plan, allergy
- Edge types: contains, recommends

## Extending the Graph
To add drug/medication information:
1. Add drug nodes with attributes (name, dosage, side effects)
2. Create edges from drugs to conditions they treat
3. Create edges from drugs to foods they interact with
4. Add nutrient interaction data where relevant

## Requirements
- Python 3.x
- NetworkX
- Pandas

Install with:
```bash
pip install networkx pandas
```