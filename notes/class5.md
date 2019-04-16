# Move fast and break things
- template Node project
    - add resource
    - resource
    - auth

## Grog
- To understand how the pieces fit together
- Find ways

## Your job is to identity what you don't know and learn what is does
- async makes sure something
- await
- to conduct error handling
- await has to be a within a function that is a promise
```
// CREATE PET
    app.post('/pets', upload.single('avatar'), async (req, res, next) => {
        console.log(req.file)
        var pet = new Pet(req.body);
        pet.save(function (err) {
            if (req.file) {
                client.upload(req.file.path, {}, function (err, versions, meta) {
                    // STATUS OF 400 FOR VALIDATIONS
                    if (err) {return res.status(400).send({ err: err }) };

                    versions.forEach(function (image) {
                        var urlArray = image.url.split('-');
                        urlArray.pop();
                        var url = urlArray.join('-');
                        pet.avatarUrl = url;
                        pet.save();
                    });

                    res.send({ pet: pet });
                });
            } else {
                res.send({ pet: pet});
            }
        });
    });
```
