###Example
<p>Consider a <code>MediaPlayer</code> interface. A concrete class <code>AudioPlayer</code> implements this interface.
<code>AudioPlayer</code> plays mp3 format audio files by default.Consider another <code>AdvancedMediaPlayer</code> interface. Concrete classes implement this interface.
This interface plays vlc and mp4 files.Our objective is to make <code>AudioPlayer</code> play other formats. Hence,an adapter 
class <code>MediaAdapter</code> is created to implement the <code>MediaPlayer</code> interface 
thorugh <code>AdvancedMediaPlayer</code>. </p>

