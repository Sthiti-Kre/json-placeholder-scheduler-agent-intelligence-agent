# Json Placeholder Scheduler Agent Intelligence Agent — Scheduler Agent

## Overview
This agent fetches data from 1 API source(s) on a schedule and stores the results in **firestore**.

## Scheduled Jobs
| # | Name | URL | Times (Asia/Kolkata) | Auth |
|---|------|-----|--------------------|------|
| 1 | Json Place holder data | https://json-placeholder.mock.beeceptor.com/posts | 12:40, 17:01 | none |

## Endpoints
| Endpoint | Method | Description |
|----------|--------|-------------|
| `/health` | GET | Health check + scheduler status |
| `/scheduler/status` | GET | All jobs with next run times + cached results |
| `/run` | POST | Manually trigger all jobs immediately |
| `/chat` | POST | Chat with the agent (uses cached data as context) |

## Setup
pip install -r requirements.txt
cp .env.example .env
# Fill in your credentials in .env
uvicorn main:app --host 0.0.0.0 --port 8080

## Memory
- In-memory cache TTL: **24h** (auto-purges after 24 hours)
- Persistent storage: **firestore** → collection `scheduler_data`