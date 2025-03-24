🔧 Changes Made
Here is a summary of the modifications made to the base GUI project:

✅ 1. Replaced deprecated dataset
Replaced the deprecated load_boston() dataset from sklearn.datasets with fetch_california_housing() to ensure compatibility with the latest versions of scikit-learn.

✅ 2. Fixed MNIST data formatting
Reshaped and normalized the MNIST dataset:

From shape (28, 28) to flat vectors (784,) using:

python
Kopyala
Düzenle
X_train.reshape(-1, 28*28).astype("float32") / 255.0
This ensures the dataset works properly with dense neural networks.

✅ 3. Ensured proper data types before training
Added conversion using np.asarray(...).astype("float32") before passing data into the model to avoid training errors.

✅ 4. Fixed duplicate train_neural_network() definition
Removed one of the duplicate train_neural_network() functions to prevent unexpected behavior and confusion.

✅ 5. Fixed Matplotlib canvas compatibility
Replaced the incompatible import:

python
Kopyala
Düzenle
from matplotlib.backends.backend_qt5agg import FigureCanvasQTAgg
with:

python
Kopyala
Düzenle
from matplotlib.backends.backend_qtagg import FigureCanvasQTAgg
This makes the GUI compatible with PyQt6 and recent versions of Matplotlib.

Additionally, added .setParent(QWidget()) to ensure FigureCanvas is treated correctly as a QWidget inside the layout.

✅ 6. Added progress bar reset at training start
Implemented on_train_begin() method in the custom Keras callback to reset the training progress bar to 0% at the beginning of model training.