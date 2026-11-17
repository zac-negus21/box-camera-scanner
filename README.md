# Box Camera Scanner

A single-page web app: scan a box label, then every item barcode in the box with the phone camera (or photos), and copy a SQL script that moves those items into the box.

Live page: https://zac-negus21.github.io/box-camera-scanner/

Everything runs in the browser. Scans and settings stay on the device; nothing is sent anywhere. The schema, barcode view, job number and your username are entered in Settings on first use and stay on that device.

## Phone as a camera

On the computer, click **Connect a phone** and scan the QR code with any phone. The phone streams its camera to the computer, which reads the barcodes. The free PeerJS service (0.peerjs.com) introduces the two devices; video then goes directly between them, or through a PeerJS relay when networks block a direct link.

## The SQL

The generated script checks the box (exists, enabled, same customer as the job), previews every scanned barcode, moves only the items that pass inside a transaction (setting BoxID, UpdateDate and UpdatedBy), and shows a final check before you COMMIT or ROLLBACK.
