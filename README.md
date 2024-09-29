## Features
- Extracts key bank card details:
  - Card Number
  - Expiration Date
  - Cardholder Name
- Uses Tesseract OCR for accurate and fast recognition.
- Simple and secure RESTful API.
- Cross-platform support, works in local or cloud environments.
- Easy to deploy and integrate into existing systems.
- Can be extended to support other types of cards (e.g., membership cards, ID cards).

## Technologies Used
- **Python**: Core programming language.
- **Flask/FastAPI**: Web framework for exposing the API.
- **Tesseract OCR**: Optical Character Recognition engine.
- **OpenCV**: For image processing and enhancement.
- **Pillow**: For image manipulation.
- **Docker**: For containerization and easy deployment.

## How to Use
```
import requests
import hashlib
import time

def generate_token(key, timestamp, secret):
    hash_string = f"{key}+{timestamp}+{secret}"
    return hashlib.md5(hash_string.encode()).hexdigest()

def make_request():
    key = "M***********g"
    secret = "3***********6"
    timestamp = int(time.time() * 1000)
    token = generate_token(key, timestamp, secret)

    files = {
        'key': (None, key),
        'typeId': (None, '17'),
        'timestamp': (None, str(timestamp)),
        'token': (None, token),
        'img': (None, "/9j")
    }

    response = requests.post('https://flyocr.com/api/recogliu.do', files=files)
    return response.text

if __name__ == '__main__':
    response_text = make_request()
    print(response_text)
    ```
    