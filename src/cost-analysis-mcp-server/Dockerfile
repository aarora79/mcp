FROM python:3.12-slim

WORKDIR /app

# Install uv (from Astral Software) for Python dependencies
RUN pip install uv

# Copy necessary files
COPY pyproject.toml README.md ./
COPY awslabs/cost_analysis_mcp_server/ /app/awslabs/cost_analysis_mcp_server/

# Install dependencies using uv
RUN uv pip install --no-cache --system -e .

# Add AWS configuration directory
#RUN mkdir -p /root/.aws

# Expose port for SSE transport
EXPOSE 8888

# Set the entrypoint to run the MCP server
ENTRYPOINT ["python", "-m", "awslabs.cost_analysis_mcp_server.server"]
# Default command if no arguments provided
CMD []