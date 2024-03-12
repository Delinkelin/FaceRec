# Face Recognition Project

This project uses Flask, FastAPI,DeepFace and MongoDB to create a Face recognition system. It allows users to register face with associated metadata, update their information and also can delete their data.

### Get started

These instructions will guide you through setting up the project and configuring MongoDB Atlas for development. 

### Prerequisites

This project requires Python 3.7 or later.

### Installing

1. Clone this repository to your local system using link

    ```bash
    git clone "https://dev.azure.com/tmspl/FaceRec/_git/FaceRec-Employee-Enrollment.python"
    ```

2. Navigate to the project directory:

    ```bash
    cd FaceRec
    ```

3. Install the required packages:

    ```bash
    pip install -r requirements.txt
    ```


### Running the Server
To start FLask and FastAPI, run the given command:
```bash
4. Set up MongoDB Atlas by following the instructions provided in the MongoDB documentation. Store your MongoDB Atlas connection string securely, preferably in environment variables or a configuration file.
python main.py
```

## Project Structure

- `requirements.txt`: Contains the Python dependencies for the project.
- `API/`: Contains code of FastAPI application.
- `FaceRec/`: Contain all files of HTML,CSS and flask application.
- `main.py`: Contains code of to start FastAPI and flask together.

## Database Schema

1. To migrate your local MongoDB data to MongoDB Atlas, first create a MongoDB Atlas account and set up a cluster.

2. Use the MongoDB Atlas Data Import tool to migrate your data from the local MongoDB instance to your MongoDB Atlas cluster.

3. Update your application's connection string to point to your MongoDB Atlas cluster. Securely store the MongoDB Atlas connection string.

The database contains a `faceEntries` collection with the following schema:

- `id`: A unique identifier for the face entry.
- `Employeecode`: A unique  employee ID associated with the image.
- `Name`: The name of the person in the image.
- `gender`: The gender of the person.
- `Department`: The department of the person
- `time`: The time the face entry was created.
- `embeddings`: The embeddings of the face image.
- `Images`: Base64 encoded image file.

## Function Flow 

1. `create_new_faceEntry()`: This function receives a POST request with an image and metadata. It extracts the face from the image, calculates the embeddings, and stores the data in the database.

2. `Data()`: This function sent a GET request  to `/data` endpoint of FastAPI app to get the list of Face Entries from MongoDB.

3. `update()` :This function is used to update the details of the face entry in the database.

4. `read()` : This function sent a GET request with specific Employeecode to read the information related to that particular Employeecode.

5. `delete()` : This function is used to delete the specific Employee Data.

To switch between using the local MongoDB instance and MongoDB Atlas, adjust the `use_cloud_db` parameter when instantiating the `Database` class. Set `use_cloud_db=True` to use MongoDB Atlas, or `use_cloud_db=False` to use the local MongoDB instance. This allows for flexible database access configuration depending on your environment or testing needs.
## Testing

To run the tests, use the following command:

```bash
pytest
```

## License

This project is licensed under the APACHE License - see the [LICENSE](LICENSE) file for details.
