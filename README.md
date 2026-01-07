# 🔬 PySpark Patent Citation Analysis

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![PySpark](https://img.shields.io/badge/PySpark-3.0+-orange.svg)](https://spark.apache.org/)

A distributed computing project using Apache Spark to analyze patent citation patterns across U.S. states. This project identifies which patents cite the most other patents from their own state (self-state citations).

## 📊 Project Overview

This project processes millions of patent records to solve the **patent join problem** - finding patents with the highest number of same-state citations. The analysis reveals geographic patterns in patent citations and demonstrates big data processing techniques.

### Problem Statement

Given:
- **~2.9 million patent records** with state information
- **~16 million citation records** linking patents

Goal:
- Determine how many patents each patent cites from its own state
- Identify the top 10 patents with the highest self-state citation counts

## 🛠️ Technologies Used

- **Apache Spark** - Distributed computing framework
- **PySpark** - Python API for Spark
- **Python 3.8+** - Primary programming language
- **Pandas** - Data display and analysis
- **Jupyter Notebook** - Interactive development environment

## 📁 Dataset

### Citations Data (`cite75_99.txt.gz`)
- Patent citation relationships (1975-1999)
- Format: `CITING, CITED`
- ~16 million citation records

### Patents Data (`apat63_99.txt.gz`)
- Patent metadata including state information (1963-1999)
- Includes: patent number, grant year, state, citation counts
- ~2.9 million patent records

## 🚀 Implementation Approaches

This project implements the solution using **two PySpark APIs** to demonstrate different programming paradigms:

### 1. DataFrame API (`Lab-04-patent-dataframe.ipynb`)
- Higher-level, SQL-like operations
- Optimized execution via Catalyst optimizer
- **Faster execution** - Recommended for production
- Uses declarative transformations

### 2. RDD API (`Lab-04-patent-rdd.ipynb`)
- Lower-level, functional programming approach
- Fine-grained control over transformations
- Educational value for understanding Spark internals
- Uses map, reduce, join operations

## 📋 Installation & Setup

1. **Clone the repository**
```bash
git clone https://github.com/vedantkesharia/pyspark-patent-citation-analysis.git
cd pyspark-patent-citation-analysis
```

2. **Install dependencies**
```bash
pip install pyspark pandas jupyter
```

3. **Download datasets**
```bash
make download  # If Makefile is configured
# Or download manually from the data source
```

4. **Launch Jupyter Notebook**
```bash
jupyter notebook
```

## 💡 Usage

### DataFrame Approach (Recommended)
```python
# Open Lab-04-patent-dataframe.ipynb
# Run all cells to see the complete analysis
```

### RDD Approach
```python
# Open Lab-04-patent-rdd.ipynb
# Run all cells to see the RDD-based implementation
```

## 📈 Key Analysis Steps

1. **Data Loading**: Read compressed CSV files using Spark
2. **Join Operations**: 
   - Link citations with cited patent states
   - Link with citing patent states
3. **Flag Self-Citations**: Identify when `cited_state == citing_state`
4. **Aggregation**: Count self-state citations per patent
5. **Ranking**: Sort and extract top 10 patents

## 🎯 Results

The analysis identifies patents with the highest number of in-state citations, revealing:
- Geographic clustering patterns in innovation
- State-level patent citation networks
- Patents with significant regional influence

**Sample Output:**
| Patent | State | Self-State Citations |
|--------|-------|---------------------|
| 5959466 | CA | 125 |
| 5983822 | TX | 103 |
| ... | ... | ... |

## 📚 Learning Objectives

- Master PySpark DataFrame and RDD APIs
- Understand distributed data processing concepts
- Implement complex join operations at scale
- Compare functional vs declarative programming in Spark
- Optimize big data workflows

## 🔧 Performance Considerations

- **Caching**: Use `.cache()` after expensive join operations
- **Sampling**: Test with data samples before full execution
- **Partitioning**: Leverage Spark's data partitioning
- **Local Mode**: Project runs in `local[*]` mode (all CPU cores)

## 📝 Project Structure

```
.
├── Lab-04-patent-dataframe.ipynb  # DataFrame implementation
├── Lab-04-patent-rdd.ipynb        # RDD implementation
├── Makefile                        # Build automation
├── README.md                       # Project documentation
├── cite75_99.txt.gz               # Citation data (download required)
└── apat63_99.txt.gz               # Patent data (download required)
```

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 👤 Author

**Vedant Kesharia**
- GitHub: [@vedantkesharia](https://github.com/vedantkesharia)

## 🙏 Acknowledgments

- University of Colorado Boulder - CSCI 4253/5253 Course
- Apache Spark Community
- Dataset sources and documentation

---

