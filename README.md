# About the Project
This was Solo project of mine.

Handwritten signature forgeries can be categorized based on their distinguishing characteristics into the following forms:

1. **Random Forgery**: Also known as simple forgery, this is created by the signer using the victim's name in their own unique manner.
2. **Unskilled Forgery**: The signer attempts to imitate the signature without prior expertise or understanding of the spelling.
3. **Skilled Forgery**: These forgeries are produced by experienced copycats or professional impostors, making them the most challenging to identify.

The system uses a database of signatures for training. This database is permitted for use and serves as a reference for analyzing and verifying other signatures. The system evaluates the claimed signature against the reference signature using various parameters, such as the Euclidean Distance in the feature space. If the absolute difference between the parameters of the original signature and the verification signature exceeds a certain threshold, the signature is recognized as counterfeit.

## How It Works

1. The system prompts the user for a User ID. 
2. The user must enter their ID, after which the system checks if the ID is registered.
   - If the User ID is not registered, the user must provide 5 sets of signatures for training purposes.
   - If the User ID is registered, the input signature image will be analyzed to determine if it is forged.
3. The input training signatures and the testing signature undergo a preprocessing stage:
   - The input training signature is saved as a reference signature in the database.
   - The input testing signature is saved as a sample signature and proceeds to the verification stage.
4. In the Verification stage, the sample signature is compared with the reference signature stored in the database. 
   - If the difference between the two signatures does not exceed the threshold values of the features in the CSV files, the sample signature is accepted as genuine.
   - If the difference does exceed the threshold, the signature is rejected as forged.

### Signature Image Path Format

The format of the signature image path in our model is: `XXXZZZ_YYY.png`

- `XXX` refers to the ID of the person who has signed the document (e.g., `-001`).
- `ZZZ` refers to the ID of the person to whom the signature actually belongs (e.g., `-001`).
- `YYY` denotes the n-th attempt.

We can verify if the model output is correct by the file name: if `XXX == ZZZ`, then the image is genuine; otherwise, the signature is forged.
