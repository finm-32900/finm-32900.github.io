# Web Authentication and Authorization

Follow along with the examples in https://github.com/jmbejara/simple_auth

## Objectives  
- Learn how to deploy a FastAPI backend on Vercel.  
- Use Clerk for authentication and authorization.  
- Serve simple HTML pages protected by authentication.  

1. **Introduction to Vercel, Clerk, and FastAPI**  
   - Overview of Vercel for serverless deployment.  
   - Clerk for authentication and user management.  
   - FastAPI as the backend framework.  

2. **Setting Up FastAPI with Vercel**  
   - Install dependencies (`fastapi`, `uvicorn`, `vercel`).  
   - Create a basic FastAPI app.  
   - Configure `vercel.json` for deployment.  
   - Deploy to Vercel.  

3. **Integrating Clerk Authentication**  
   - Create a Clerk account and set up an application.  
   - Configure Clerk’s authentication middleware.  
   - Verify JWT tokens in FastAPI routes.  

4. **Serving Protected HTML Pages**  
   - Use FastAPI to serve static HTML.  
   - Restrict access to authenticated users.  
   - Implement role-based authorization.  

5. **Testing and Final Deployment**  
   - Verify authentication flow with Clerk.  
   - Test authorization with protected routes.  
   - Finalize and deploy the app.  



## Building Web Applications

In quantitative finance, delivering analysis and interactive tools to stakeholders often requires creating web applications. This lesson explores how to build web applications using FastAPI, a modern Python web framework known for its performance and ease of use.

### Simple HTML Deployment

The simplest way to share content on the web is through static HTML files. Example 0 (`ex0_simple_html`) demonstrates a basic HTML file that can be deployed directly to hosting platforms like Vercel without any server-side processing.

```{note} Example: Static HTML Deployment
Static HTML files require no server-side processing and can be deployed to platforms like Vercel with minimal configuration. This approach works well for simple, unchanging content but lacks dynamic capabilities.
```

### Basic FastAPI Server

Example 1 (`ex1_hello`) introduces FastAPI by creating a simple "Hello, World!" application. This example demonstrates the fundamental structure of a FastAPI application.

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"Hello": "World"}
```

This creates a basic API endpoint that returns a JSON response. While simple, this approach requires a traditional server deployment and won't work on serverless platforms like Vercel without additional configuration.

### Template-Based Rendering

Example 2 (`ex2_templates`) extends the basic FastAPI application by incorporating Jinja2 templates. This allows for server-side rendering of HTML content.

```python
from fastapi import FastAPI, Request
from fastapi.templating import Jinja2Templates

app = FastAPI()
templates = Jinja2Templates(directory="templates")

@app.get("/")
def read_root(request: Request):
    return templates.TemplateResponse("index.html", {"request": request})
```

This approach enables more complex HTML generation with dynamic content but still requires traditional server deployment.

### Serving Static Files

Example 3 (`ex3_static_files`) demonstrates how to serve static files with FastAPI, making it compatible with serverless platforms like Vercel.

```python
from fastapi import FastAPI
from fastapi.staticfiles import StaticFiles

app = FastAPI()
app.mount("/", StaticFiles(directory="main", html=True), name="main")
```

By mounting a directory of static files, this approach combines the simplicity of static HTML with the routing capabilities of FastAPI. This method works well on serverless platforms while providing a path to more complex functionality.

### Serving Documentation with Sphinx

Example 4 (`ex4_sphinx`) shows how to serve Sphinx-generated documentation through FastAPI. Sphinx is a powerful documentation generator commonly used in Python projects, including quantitative finance libraries.

The example mounts the HTML files generated by Sphinx, allowing for sophisticated documentation with features like:
- Syntax highlighting for code examples
- Mathematical equation rendering
- Cross-referencing between documents
- Responsive design for different devices

This approach is particularly valuable for quantitative finance applications where complex mathematical concepts and code examples need clear documentation.

### Basic Authentication

Example 5 (`ex5_simple_auth`) introduces authentication to protect sensitive content. This is crucial for financial applications where data security is paramount.

The example uses the Clerk Python SDK to add authentication to the FastAPI application, demonstrating how to:
- Verify user identity
- Control access to protected resources
- Integrate with modern authentication providers

### Advanced Authentication with Sphinx

Examples 6 and 7 (`ex7_sphinx_auth`) combine the documentation capabilities of Sphinx with authentication, creating a secure platform for sharing quantitative finance analysis and tools.

This approach is ideal for:
- Proprietary trading strategies
- Client-specific financial models
- Research that requires controlled access

### Implementation Considerations

When building web applications for quantitative finance, several factors should guide your choice of approach:

1. **Complexity of content**: Static HTML for simple content, Sphinx for complex documentation
2. **Update frequency**: Static deployment for stable content, server-based for frequently changing data
3. **Security requirements**: Authentication for sensitive financial information
4. **Computational needs**: Server-based deployment for applications requiring significant computation
5. **Deployment constraints**: Serverless platforms for simplicity, traditional servers for complex processing

### Environment Setup

The repository includes configuration for both `conda` and `pip` environments:

```bash
# Using conda
conda create -n fastapi python=3.12
conda activate fastapi

# Using pip
pip install -r requirements.txt
```

For reproducible environments, the repository maintains both `environment.yml` (for conda) and `requirements.txt` (for pip), ensuring consistent deployment across development and production environments.

### Conclusion

FastAPI provides a flexible foundation for building web applications in quantitative finance, from simple API endpoints to complex, authenticated documentation systems. By choosing the appropriate approach based on your specific requirements, you can efficiently deliver financial analysis and tools to stakeholders.
