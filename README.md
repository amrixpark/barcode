# barcode
barcode detection in python
import cv2
from pyzbar import pyzbar
path="C:/Users/AMRIX/Downloads/QRCodeBarcode.png"
img=cv2.imread(path)

barcodes=pyzbar.decode(img)

for barcode in barcodes:
    x,y,w,h=barcode.rect
    cv2.rectangle(img,(x,y),(x+w,y+h),(255,0,0),2)

    bdata=barcode.data.decode('utf-8')
    btype=barcode.type
    text=f"{bdata},{btype}"
    cv2.putText(img,text,(x-10,y-10),cv2.FONT_HERSHEY_SIMPLEX,0.5,(0,255,0),2)
cv2.imshow("Barcode reader",img)
cv2.waitKey(0)
cv2.destroyAllWindows()
