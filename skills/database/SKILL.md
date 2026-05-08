---
name: database
description: Relational database schema design, normalization, indexing, and query optimization. Use when the user says "design the schema for X", "how should this table be structured", "this query is slow", "do I need an index here", "denormalize this", or when starting a new feature that needs persistence. Covers Postgres, MySQL, SQLite. Do NOT use for ORM-specific syntax — covers conceptual design first, ORM second.
---
Provide database design expertise for schema architecture, migration management, query optimization, and scaling strategies for MySQL, PostgreSQL, and relational databases.

## Core Database Domains

**Schema Design**: Create normalized database schemas with:
- Proper relationships (one-to-one, one-to-many, many-to-many)
- Data integrity constraints (foreign keys, unique constraints, check constraints)
- Appropriate data types and indexes
- Denormalization strategies when performance requires it

**Migration Management**: Design safe, reversible database migrations with:
- Forward (up) and backward (down) migration paths
- Data transformation strategies for complex changes
- Rollback procedures for failed migrations
- Version control and deployment safety

**Performance Optimization**: Optimize database performance through:
- Query analysis with EXPLAIN plans
- Strategic indexing (single-column, composite, covering, partial)
- N+1 query problem resolution
- Connection pooling and query caching
- Slow query identification and remediation

**Scalability Planning**: Design for growth with:
- Read replicas for horizontal scaling
- Vertical and horizontal partitioning strategies
- Sharding for massive datasets
- Connection pooling and load balancing
- Cache-aside patterns with Redis/Memcached

**Data Security & Compliance**: Implement security measures:
- Column-level encryption for sensitive data
- Row-level security policies
- Audit logging for compliance (GDPR, HIPAA)
- Access control and privilege management
- Secure backup and recovery strategies

**Archival & Retention**: Manage data lifecycle with:
- Time-based archival strategies
- Partitioning by date for efficient archival
- Automated archival procedures
- Compliance-driven retention policies

## Example Schema Pattern

```sql
CREATE TABLE users (
    id BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
    email VARCHAR(255) NOT NULL UNIQUE,
    password_hash VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    deleted_at TIMESTAMP NULL, -- Soft deletes

    INDEX idx_email (email),
    INDEX idx_created_at (created_at),
    INDEX idx_deleted_at (deleted_at)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;
```

Provide specific SQL examples, migration code, index recommendations with EXPLAIN plan analysis, scaling architecture diagrams, and performance benchmarks where applicable.
