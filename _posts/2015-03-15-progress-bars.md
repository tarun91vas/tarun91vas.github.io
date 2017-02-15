---
layout: post
title: Progress bars for AJAX request
subtitle: Percentage of data received
tags: [progress bars, ajax]
---

Progress bars are really interesting. It keeps the user's curiosity to monitor the completion of api request. Requests can be light or heavy (e.g downloading large file) depending on the application taking less or more time respectively. Long waiting time can not only ruin the user experience but confuse them regarding functionality of web application. That's why we use progress bars to engage them.

In this article, I will give a seed code and quick walk through the same to integrate bootstrap progress bars for AJAX requests. The idea is simple, we have to monitor the on progress event and according to the percentage of data received modify the width of the progress bar. Read more <a href="https://developer.chrome.com/native-client/devguide/coding/progress-events" target="_blank">here</a>.

The JavaScript function to update the progress bars is given below :

{% highlight javascript linenos %}
function updateProgress() {
    var bar = $('#mybar');
    // Lets pick a sample url of google maps api. Use your URL
    var url = 'https://maps.googleapis.com/maps/api/streetviewsize=400x400&amp;location=40.720032,-73.988354&amp;fov=90&amp;heading=235&amp;pitch=10'
    var xhr = new XMLHttpRequest();
    xhr.open("GET", url, true);
    xhr.responseType = "document";

    xhr.addEventListener("load", function () {
        if (xhr.status === 200) {

        // Do something..
        alert('Reqeuest Completed !!');
        } else {
        alert('Error making the request');
        }
    }, false);

    var prev_percent = 0;
    xhr.addEventListener("progress", function(event) {
        if (event.lengthComputable) {

            // Update progress bars
            var percent = Math.round((event.loaded / event.total) * 100);
            if (percent != prev_percent) {
                prev_percent = percent;
                bar.css('width', percent+"%");
                bar.html(percent+"%");
            }
       }
   });
   xhr.send();
}
{% endhighlight %}

<a href="https://github.com/tarun91vas/Progress-bars-AJAX" target="_blank">View on github</a>

Above function uses  <strong>lengthComputable</strong>,<strong> loaded</strong> and <strong>total</strong> attribute of progress event to calculate the percentage of event loaded. I tested this code for a simple URL where the request was very fast. You can try with different urls with greater response time and notice the change.




