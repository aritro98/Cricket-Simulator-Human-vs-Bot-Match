# AI Driven Cricket Simulation Human vs Bot T20 Match

This repository implements a command‐line based T20 cricket simulation. Users can define teams, execute matches with realistic ball-by-ball outcomes, and persist match data in a MySQL database. The simulator is designed for ease of setup, extensibility, and clear presentation of match statistics.

## Overview
It is a console-based T20 cricket simulator where a human-managed team (Team A) faces off against an AI-driven bot team (Team B). It provides:
- A menu-driven interface for team creation, match setup, and score viewing.
- Realistic ball-by-ball simulation with random scoring events (runs, fours, sixes, wickets).
- Persistent storage of match metadata and player performance in a MySQL database (`cricketdb`).
- Tabular scoreboards and final summaries printed in the terminal.

## Prerequisites & Dependencies
- **Python** ≥ 3.8
- **MySQL Server** (with `cricketdb` schema)
- **Python Packages:**
  - `mysql-connector-python`
  - `prettytable`

Install Python packages via pip:
```bash
pip install mysql-connector-python prettytable
```

## Installation and Setup
1. Create database in your MySQL server:
   ```sql
   CREATE DATABASE cricketdb;
   ```