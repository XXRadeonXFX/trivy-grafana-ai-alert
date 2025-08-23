# prompt = f"""
        #     You are a Security and DevSecOps expert. I am using the following Dockerfile:

        #     {DOCKERFILE_CONTENT}

        #     I ran a vulnerability scan and found these CVEs:
        #     {request.cve_name}

        #     Your task:
        #     1. For each unique CVE, give a short, simple explanation of the issue.
        #     2. Provide the exact fix command (e.g., apt-get install <package>=<fixed-version> or pip install <package>==<version>).
        #     3. Group CVEs if the same package upgrade fixes multiple issues.
        #     4. Show HIGH severity CVEs and their fixes first.
        #     5. Output should ONLY be in HTML Format:
        #     - CVE-ID → Short explanation → Fix command
        #     6. If the CVE is not fixed yet, then show the list of CVE which is not fixed after the docker snippet
            

        #     👉 Example of expected response format:

        #     CVE-2025-1390 → Python buffer overflow → apt-get install libpython3.8=3.8.18-2+deb12u3

        #     CVE-2025-24528, CVE-2024-26462 → zlib vulnerabilities → apt-get install zlib1g=1:1.2.13.dfsg-1+deb12u3

        #     CVE-2025-32988 → OpenSSL heap overflow → apt-get install libssl1.1=1.1.1n-0+deb12u3


        #     ✅ Then at the bottom, a ready-to-use Dockerfile snippet like:

        #     RUN apt-get update && apt-get install -y \
        #         libpython3.8=3.8.18-2+deb12u3 \
        #         zlib1g=1:1.2.13.dfsg-1+deb12u3 \
        #         libssl1.1=1.1.1n-0+deb12u3 \
        #         && rm -rf /var/lib/apt/lists/*
                        
        # """