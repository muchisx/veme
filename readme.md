var tag = document.createElement('script');
    tag.src = "https://www.youtube.com/iframe_api";
    var firstScriptTag = document.getElementsByTagName('script')[0];
    firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);

    var player;
      function onYouTubeIframeAPIReady() {
        player = new YT.Player('player', {
          height: '100%',
          width: '100%',
          playerVars: { 'autoplay': 1, 'controls': 0, 'loop':1, 'playlist': 'PX9-us-1t4I', 'mute':1 ,'autohide':1, 'fs':1,'disablekb':1 },
          videoId: 'PX9-us-1t4I',
          events: {
            'onReady': onPlayerReady,
          }
        });
      }
      function onPlayerReady(event) {
        event.target.playVideo();
      }
      var done = false;
      function onPlayerStateChange(event) {
        if (event.data == YT.PlayerState.PLAYING && !done) {
          setTimeout(stopVideo, 6000);
          done = true;
        }
      }
      function stopVideo() {
        player.stopVideo();
        player.playVideo();
      }

      $('.ytp-large-play-button.ytp-button').trigger('click');

      $(function() {
            var video = $("#someVideo").get(0);

            fakeClick(function() {
              player.playVideo();
            });
        });