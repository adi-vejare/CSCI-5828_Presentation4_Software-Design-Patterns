###Example
<p>Consider a <code>MediaPlayer</code> interface. A concrete class <code>AudioPlayer</code> implements this interface.
<code>AudioPlayer</code> plays mp3 format audio files by default.Consider another <code>AdvancedMediaPlayer</code> interface. Concrete classes implement this interface.
This interface plays vlc and mp4 files.Our objective is to make <code>AudioPlayer</code> play other formats. Hence,an adapter 
class <code>MediaAdapter</code> is created to implement the <code>MediaPlayer</code> interface 
thorugh <code>AdvancedMediaPlayer</code>. </p>

[<img src="https://cloud.githubusercontent.com/assets/14101008/11768481/3b7d20d6-a18b-11e5-95fe-a422966f4c03.png" width="50" height="50"></img>](https://github.com/hariniiyer/CSCI-5828_Presentation4_Software-Design-Patterns/blob/master/AdapterFeatures.md)
[<img src="https://cloud.githubusercontent.com/assets/14101008/11768482/3d2d0bbc-a18b-11e5-8766-2e7f5b241782.png" width="50" height="50"></img>](https://github.com/hariniiyer/CSCI-5828_Presentation4_Software-Design-Patterns/blob/master/AdapterCode.md)
