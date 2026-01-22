# Inventory Allocation System

> A production-grade demonstration of concurrent inventory allocation across multiple warehouses, solving the critical e-commerce challenge of preventing overselling when multiple customers order simultaneously.

## Table of Contents
- [Problem Statement](#problem-statement)
- [Solution Overview](#solution-overview)
- [Key Features](#key-features)
- [Technical Architecture](#technical-architecture)
- [Getting Started](#getting-started)
- [Allocation Approach](#allocation-approach)
- [Data Model](#data-model)
- [Concurrency Handling](#concurrency-handling)
- [Example Scenarios](#example-scenarios)
- [API Documentation](#api-documentation)
- [Running Tests](#running-tests)
- [Technologies Used](#technologies-used)

## Problem Statement

Design a system that allocates stock to customer orders without overselling when multiple orders are placed simultaneously. The system must:

- Support one or more warehouses
- Use SQL database for persistence
- Handle orders placed via API
- Prevent race conditions and overselling
- Maintain data integrity under concurrent load

**The Core Challenge:**  
When two customers simultaneously order the last item in stock, how do you ensure only one order succeeds while the other receives accurate "out of stock" feedback—without any overselling or data corruption?

## Solution Overview

This system implements a **transaction-based allocation engine** with proper concurrency controls to guarantee safe stock allocation across multiple warehouses. It uses database-level locking mechanisms, isolation levels, and idempotent operations to prevent the classic inventory race condition.

### What Makes This Solution Production-Ready?

**Prevents Overselling** - Database transactions and row-level locking ensure atomic allocation  
**Handles Concurrency** - Multiple simultaneous orders are processed safely  
**Multi-Warehouse Support** - Allocates from available warehouses intelligently  
**Data Integrity** - Proper constraints and validation prevent invalid states  
**Idempotent Operations** - Retry-safe allocation prevents duplicate reservations  
**Clear Audit Trail** - Every allocation decision is tracked and traceable