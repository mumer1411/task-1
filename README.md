# task-1
computer vision task 1 applying openCV

import cv2 as cv

img = cv.imread(r'C:\Users\Umer Farooq\Desktop\AI ML\football.jpg')
cv.imshow('football', img)

gray = cv.cvtColor(img, cv.COLOR_BGR2GRAY)
cv.imshow('Gray', gray)
cv.waitKey(0)
cv.destroyAllWindows()


def process_media(football.jpg, mountains.mp4, outputvid.mp4):
  # 1. Read an image
  img = cv2.imread(football.jpg)
  if img is None:
    print(f"Warning: Could not read image from {football.jpg}")
  else:
    print(f"Successfully loaded image: {football.jpg}")

  # 2. Open the input video
  cap = cv2.VideoCapture(r'C:\Users\Umer Farooq\Downloads\mountains.mp4')
  if not cap.isOpened():
    print(f"Error: Could not open video {r'C:\Users\Umer Farooq\Downloads\mountains.mp4'}")
    return

  # Extract video properties for the writer
  frame_width = int(cap.get(cv2.CAP_PROP_FRAME_WIDTH))
  frame_height = int(cap.get(cv2.CAP_PROP_FRAME_HEIGHT))
  fps = cap.get(cv2.CAP_PROP_FPS)

  # 3. Setup VideoWriter to save the output video
 
  fourcc = cv2.VideoWriter_fourcc(*"mp4v")
  out = cv2.VideoWriter( r'C:\Users\Umer Farooq\Downloads\outputvid.mp4', fourcc, fps, (frame_width, frame_height)
  )

  print("Processing video frames...")

  while cap.isOpened():
    ret, frame = cap.read()
    if not ret:
      break  # End of video

    # 4. Draw a box on the frame
    
    start_point = (50, 50)
    end_point = (300, 300)
    box_color = (0, 255, 0)  # Green in BGR format
    thickness = 3
    cv2.rectangle(frame, start_point, end_point, box_color, thickness)

    # 5. Write text on the frame
   
    text = "Karvan-e-Haramain"
    org = (55, 40)  # Position just above the box
    font = cv2.FONT_HERSHEY_SIMPLEX
    font_scale = 0.8
    text_color = (255, 255, 255)  # White in BGR format
    cv2.putText(
        frame, text, org, font, font_scale, text_color, 2, cv2.LINE_AA
    )

    # Write the modified frame into the output video
    out.write(frame)

  # Release resources cleanly
  cap.release()
  out.release()
  cv2.destroyAllWindows()
  print(f"Output video successfully saved to: {outputvid.mp4}")
