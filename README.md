# NodeJS_FileUpload

-> we can put into form html element file picker
	-> enctype="multipart/form-data" form argument

-> multer
	-> parser, that parses file requests or mixed
		(body-parser can only parse text)

multer.diskstorage({
	...
})

Files should not be stored in a database, 
but in a filesystem. Save path and some info.

req.file objekt we are using

-> we can serve images statically (public for everyone)

-> we can use fs.readFile(path, function(..., data) => {
	res.setHeader('Content-Type', '...')
	res.setHeader('Content-Disposition, 'inline; filename= ...')
		we can change inline to attachment and browser wont open 
		it in window, but download.
	res.send(data)

	})

	Problem is, that nodejs in this case first copys all data
	in memory. Lets rather use ReadStream.

-> fs.createReadStream(path) 
	file.pipe(res)

In this case we directly pipe data to response object. Node doesnt
have to store an entire file. Browser concatenates data chunks
into a file. 

-> PDFKit for creating documents.

-> fs.createWriteStream(path) saves stream to server

-> fs.unlink() deletes a file.

