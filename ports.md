# Port Management

The current open ports are listed below. The services that run on these ports are visible through `.env` file.

| TCP PORT | UDP PORT |
|----------|----------|
|   80     |  5680    |
|   8080   |  5681    |
|   8081   |  5682    |
|   8082   |  5683    |
|   8083   |  5684    |
|   8084   |  5685    |
|   8085   |  5686    |
|   8086   |  5687    |
|   8087   |  5688    |
|   8088   |  5689    |
|   8089   |  -       |
|   5685   |  -       |

**Jaeger Service Ports:**
- 8084: Jaeger UI (maps to internal 16686)
- 8085: Jaeger Collector (maps to internal 14268)  
- 5689: Jaeger Agent UDP (maps to internal 5689)
