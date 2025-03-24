🔧 Changes Made
Here is a structured summary of the modifications made to the base GUI project:

✅ 1. 🗂️ Replaced Deprecated Dataset
🔄 Replaced the deprecated load_boston() dataset from sklearn.datasets with fetch_california_housing()
📦 This ensures compatibility with the latest versions of scikit-learn.

✅ 2. 🧮 Fixed MNIST Data Formatting
📐 The MNIST dataset was reshaped and normalized:

X_train.reshape(-1, 28*28).astype("float32") / 255.0
🔍 Converted 28x28 images to flat 784-length vectors.
📊 This ensures proper input format for dense neural networks.

✅ 3. 🔄 Ensured Data Type Consistency Before Training
💡 Added conversion using:

np.asarray(...).astype("float32")
🛡️ This prevents data type mismatches during model training and improves stability.

✅ 4. 🧯 Removed Duplicate Method Definition
🧹 Removed the duplicate train_neural_network() function.
🎯 This prevents unexpected behavior and makes the code cleaner and more maintainable.

✅ 5. 🖼️ Fixed Matplotlib Canvas Compatibility
🔁 Replaced incompatible backend import:

from matplotlib.backends.backend_qt5agg import FigureCanvasQTAgg
✨ With the PyQt6-compatible version:

from matplotlib.backends.backend_qtagg import FigureCanvasQTAgg
🧷 Also added .setParent(QWidget()) to treat the canvas properly as a QWidget in the layout.

✅ 6. 📊 Added Progress Bar Reset at Training Start
🧠 Implemented on_train_begin() method inside a custom Keras callback:

def on_train_begin(self, logs=None):
    self.progress_bar.setValue(0)
📍 This resets the progress bar to 0% at the beginning of each training session, improving user feedback and experience.