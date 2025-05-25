# Cricket Simulator: Human vs Bot T20 Match

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
2. Define tables (run these in your MySQL client):
   ```sql
   -- Match metadata
   CREATE TABLE GAME (
     MID INT PRIMARY KEY AUTO_INCREMENT,
     MNAME VARCHAR(20) NOT NULL,
     OVERS INT NOT NULL,
     WINNER CHAR(1),
     IS_DRAW CHAR(1),
     BATSFIRST CHAR(1)
   );

   -- Human team scores
   CREATE TABLE SCOREA (
     RUNS INT,
     FOURS INT,
     SIXES INT,
     BALLS INT,
     PNAME VARCHAR(30) PRIMARY KEY
   );

   -- Bot team scores
   CREATE TABLE SCOREB (
     RUNS INT,
     FOURS INT,
     SIXES INT,
     BALLS INT,
     PNAME VARCHAR(30) PRIMARY KEY
   );

   -- Team rosters
   CREATE TABLE TEAM1 (
     PID CHAR(3) PRIMARY KEY,
     PNAME VARCHAR(25) NOT NULL,
     TYPE VARCHAR(25),
     TNAME CHAR(1) DEFAULT 'A'
   );
   CREATE TABLE TEAM2 (
     PID CHAR(3) PRIMARY KEY,
     PNAME VARCHAR(25) NOT NULL,
     TYPE VARCHAR(25),
     TNAME CHAR(1) DEFAULT 'B'
   );
   ```
3. Ensure the MySQL user configured in `game.py` has privileges on `cricketdb`.

## Usage
1. Clone the repository:
   ```bash
   git clone https://github.com/aritro98/AI-Driven-Cricket-Simulation-Human-vs-Bot-T20-Match.git
   ```
2. Navigate to the project directory:
   ```bash
   cd AI-Driven-Cricket-Simulation-Human-vs-Bot-T20-Match
   ```
3. Configure database credentials in `game.py` (host, user, password).
4. Run the simulator:
   ```bash
   python game.py
   ```
5. Follow on-screen menu to:
   - Create or load teams
   - Start a match (with coin toss)
   - View live scoreboards
   - View final summary and winner