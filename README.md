# google-drive-upload-with-node.js
upload files to google drive with google-apis

-------------------------------------------------



/*


var { google } = require("googleapis");
var drive = google.drive("v3");
var key = require("../private_key.json");
var path = require("path");
var fs = require("fs");

var jwToken = new google.auth.JWT(
  key.client_email,
  null,
  key.private_key,
  ["https://www.googleapis.com/auth/drive"],
  null
);

jwToken.authorize(authErr => {
  if (authErr) {
    console.log("error : " + authErr);
    return;
  } else {
    console.log("Authorization accorded");
  }
});


var PastaPublica = "trhfhdyjgdj";
var fileMetadata = {
  name: "Pasta Usuario 1",
  parents: [PastaPublica],
  mimeType: "application/vnd.google-apps.folder"
};

drive.files.create(
  {
    auth: jwToken,
    resource: fileMetadata,
    fields: "id"
  },
  function(err, file) {
    if (err) {
      // Handle error
      console.error(err);
    } else {
      console.log("Folder Id: ", file.data.id);

      var fileMetadata = {
        name: "texto.txt",
        parents: [file.data.id]
      };
      var media = {
        mimeType: "text/plain",
        body: fs.createReadStream(path.join(__dirname, "./text.txt"))
      };
      drive.files.create(
        {
          auth: jwToken,
          resource: fileMetadata,
          media: media,
          fields: "id"
        },
        function(err, file) {
          if (err) {
            // Handle error
            console.error(err);
          } else {
            console.log("File Id: ", file.data.id);
          }
        }
      );
    }
  }
);

*/
