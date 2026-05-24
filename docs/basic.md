# Image Processing Basics

- OpenCV `cv2` uses BGR color format by default (`cv2.COLOR_RGB2BGR`)
- Most deep learning models including `YOLO`  expect RGB images.
- When reading images using OpenCV, convert BGR → RGB before feeding into `YOLO` (cv2.cvcolor(img, cv2.COLOR_BGR2RGB))

```py
img = cv2.imread("image.jpg")   # BGR
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```

- Pillow (`PIL`) reads images in RGB format
- CV2 was built early days so camera hardware and old library return BGR order by default

> OpenCV stores and processes images in BGR format by default

| Library                     | Default Color Order |
| --------------------------- | ------------------- |
| OpenCV (`cv2`)              | BGR                 |
| Pillow (`PIL`)              | RGB                 |
| Matplotlib                  | RGB                 |
| YOLO / PyTorch / TensorFlow | RGB                 |

If you display OpenCV image directly using matplotlib:

```py
plt.imshow(img)
```

> colors look weird (blue ↔ red swapped).

better

```py
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
```

Why This Matters in YOLO

Wrong color order can:

- reduce accuracy
- hurt inference quality
- create inconsistent training results

Most modern YOLO implementations based on the Ultralytics codebase internally handle BGR → RGB conversion when images are loaded through their official APIs.

But if you do custom preprocessing using OpenCV:
then converting manually is still safest:

```py
img = cv2.imread("image.jpg")  # BGR
img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```
