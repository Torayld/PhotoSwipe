
add request to swipebox_fullscreen.js

showHideAnimationType: 'none',
pinchToClose: false,
closeOnVerticalDrag: false,
preload: [1, 1],

// Add function that returns promise
openPromise: getFullscreenPromise,

// Append PhotoSwipe to our container
appendToEl: fullscreenAPI ? pswpContainer : document.body,

// disable opening/closing animations
showAnimationDuration: 0,
hideAnimationDuration: 0,

// Add if you're using responsive images
// since viewport size is unpredictable
// at initialization
preloadFirstSlide: false
};

const lightbox = new PhotoSwipeLightbox(options);

lightbox.on('close', () => {
	pswpContainer.style.display = 'none';
	if (fullscreenAPI && fullscreenAPI.isFullscreen()) {
	  fullscreenAPI.exit();
	}
});