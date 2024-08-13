import sys
import os
import platform
import subprocess

def check_python_version():
    version = sys.version_info
    if version.major < 3 or (version.major == 3 and version.minor < 7):
        return f"Python version is {version.major}.{version.minor}.{version.micro}. Please upgrade to Python 3.7 or higher."
    return f"Python version is {version.major}.{version.minor}.{version.micro}. Good to go!"

def check_libraries():
    libraries = ["numpy", "pandas", "requests"]
    missing_libraries = []
    for lib in libraries:
        try:
            __import__(lib)
        except ImportError:
            missing_libraries.append(lib)
    
    if missing_libraries:
        return f"Missing libraries: {', '.join(missing_libraries)}. Please install them using pip."
    return "All essential libraries are installed."

def check_disk_space():
    total, used, free = shutil.disk_usage("/")
    free_space_gb = free // (2**30)
    if free_space_gb < 1:
        return f"Low disk space: Only {free_space_gb} GB free. Please free up some space."
    return f"Disk space is sufficient: {free_space_gb} GB free."

def check_network():
    try:
        response = subprocess.check_call(
            ["ping", "-c", "1", "google.com"],
            stdout=subprocess.DEVNULL,
            stderr=subprocess.DEVNULL
        )
        return "Network is reachable."
    except subprocess.CalledProcessError:
        return "Network is unreachable. Please check your connection."

def main():
    print("Checking Python environment health...")
    print(check_python_version())
    print(check_libraries())
    print(check_disk_space())
    print(check_network())

if __name__ == "__main__":
    main()
