-- tricolor_trends_schema.sql
-- Run: psql -d yourdb -f tricolor_trends_schema.sql

CREATE EXTENSION IF NOT EXISTS "uuid-ossp";

-- Users
CREATE TABLE users (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  name TEXT,
  phone TEXT UNIQUE NOT NULL,
  email TEXT,
  kyc_status TEXT DEFAULT 'none',
  wallet_balance NUMERIC(14,2) DEFAULT 0,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT now()
);

-- Wallet transactions (audit)
CREATE TABLE wallets (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  amount NUMERIC(14,2) NOT NULL,
  type TEXT NOT NULL, -- credit / debit
  reason TEXT,
  txn_ref TEXT,
  status TEXT DEFAULT 'completed',
  created_at TIMESTAMP WITH TIME ZONE DEFAULT now()
);

-- Matches
CREATE TABLE matches (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  sport TEXT NOT NULL,
  external_match_id TEXT, -- for future integration with feed providers
  team_a TEXT,
  team_b TEXT,
  start_time TIMESTAMP WITH TIME ZONE,
  status TEXT DEFAULT 'upcoming', -- upcoming | live | finished
  meta JSONB DEFAULT '{}',
  created_at TIMESTAMP WITH TIME ZONE DEFAULT now()
);

-- Contests
CREATE TABLE contests (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  match_id UUID REFERENCES matches(id) ON DELETE CASCADE,
  title TEXT,
  entry_fee NUMERIC(14,2) DEFAULT 0,
  prize_pool NUMERIC(14,2) DEFAULT 0,
  spots INTEGER DEFAULT 0,
  joined_count INTEGER DEFAULT 0,
  rules JSONB DEFAULT '{}',
  status TEXT DEFAULT 'open', -- open | closed | running | settled
  created_at TIMESTAMP WITH TIME ZONE DEFAULT now()
);

-- Teams (fantasy teams / contest entries)
CREATE TABLE teams (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  contest_id UUID REFERENCES contests(id) ON DELETE CASCADE,
  players JSONB, -- list of players / picks
  points NUMERIC DEFAULT 0,
  rank INTEGER,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT now()
);

-- Predictions (non-fantasy quick-prediction markets)
CREATE TABLE predictions (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  match_id UUID REFERENCES matches(id) ON DELETE CASCADE,
  choice JSONB, -- e.g. {"winner":"team_a"}
  stake NUMERIC(14,2) DEFAULT 0,
  outcome TEXT DEFAULT 'pending', -- pending | won | lost | refunded
  reward NUMERIC(14,2) DEFAULT 0,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT now()
);

-- Transactions (generic)
CREATE TABLE transactions (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  amount NUMERIC(14,2),
  kind TEXT, -- deposit/withdraw/contest_entry/payout
  status TEXT DEFAULT 'pending',
  gateway_ref TEXT,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT now()
);

-- Referrals
CREATE TABLE referrals (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  referrer_id UUID REFERENCES users(id),
  referred_id UUID REFERENCES users(id),
  bonus_amount NUMERIC(14,2) DEFAULT 0,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT now()
);

-- Admin audit
CREATE TABLE admin_audit (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  admin TEXT,
  action TEXT,
  details JSONB,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT now()
);

-- Indexes for performance
CREATE INDEX idx_matches_start_time ON matches (start_time);
CREATE INDEX idx_contests_match_id ON contests (match_id);
CREATE INDEX idx_teams_contest_id ON teams (contest_id);
CREATE INDEX idx_wallets_user_id ON wallets (user_id);
