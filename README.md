var express = require('express');
var http=require('http');
var app = express();
var cors = require('cors');
var bodyParser = require('body-parser');
var urlencodedParser = bodyParser.urlencoded({ extended: false })

app.use(bodyParser.json());

app.use(cors());
app.get('*', function (req, res) {
    var options = {
        hostname: '119.29.214.107',
        port: 3000,
        path: req.url,
        method: req.method
    };
    let request = http.request(options, (response) => {
        response.setEncoding('utf8');
        response.pipe(res)
        response.on('end', () => {
            console.log('done');
        });
    });
    request.end();

});
var server = app.listen(8001, function (req,res) {
    var host = server.address().address;
    var port = server.address().port;

    console.log('Example app listening at http://%s:%s', host, port);
  });


