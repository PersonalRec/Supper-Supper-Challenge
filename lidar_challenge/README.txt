1. Create the conda environment:
    conda create -n pdal_env
2. Activate the conda environment:
    conda activate pdal_env
3. Install PDAL for the python environment:
    conda install -c conda-forge pdal python-pdal
4. Create a pipeline.json file for PDAL:
    {
  "pipeline": [
    {
      "type": "readers.las",
      "filename": "./input.las"
    },
    {
      "type": "filters.smrf",
      "scalar": 1.25,
      "slope": 0.15,
      "threshold": 0.5,
      "window": 16.0
    },
    {
      "type": "filters.range",
      "limits": "Classification[2:2]"  # Keep only ground points
    },
    {
      "type": "writers.las",
      "filename": "ground_points.las"
    }
  ]
    }
5. Execute the pipeline using PDAL:
    pdal pipeline pipeline.json
6. Visualize the results by running the code in the lidar.ipynb file.