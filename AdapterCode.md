###Code
<b>Interface for <code>MediaPlayer</code> </b>
<pre><code>public interface MediaPlayer {
   public void play(String audioType, String fileName);
}</code></pre>

<b>Interface for <code>AdvancedMediaPlayer</code></b>
<pre><code>public interface AdvancedMediaPlayer {	
   public void playVlc(String fileName);
   public void playMp4(String fileName);
}</code></pre>

<b>Concrete class <code>VlcPlayer</code></b> 
<pre><code>public class VlcPlayer implements AdvancedMediaPlayer{
   @Override
   public void playVlc(String fileName) {
      System.out.println("Playing vlc file. Name: "+ fileName);		
   }

   @Override
   public void playMp4(String fileName) {
      //do nothing
   }
}</code></pre>

<b>Concrete class <code>Mp4Player</code></b> 
<pre><code>public class Mp4Player implements AdvancedMediaPlayer{

   @Override
   public void playVlc(String fileName) {
      //do nothing
   }

   @Override
   public void playMp4(String fileName) {
      System.out.println("Playing mp4 file. Name: "+ fileName);		
   }
}</code></pre>

<b>Adapter Class <code>MediaAdapter</code></b>
<pre><code>public class MediaAdapter implements MediaPlayer {

   AdvancedMediaPlayer advancedMusicPlayer;

   public MediaAdapter(String audioType){
   
      if(audioType.equalsIgnoreCase("vlc") ){
         advancedMusicPlayer = new VlcPlayer();			
         
      }else if (audioType.equalsIgnoreCase("mp4")){
         advancedMusicPlayer = new Mp4Player();
      }	
   }

   @Override
   public void play(String audioType, String fileName) {
   
      if(audioType.equalsIgnoreCase("vlc")){
         advancedMusicPlayer.playVlc(fileName);
      }
      else if(audioType.equalsIgnoreCase("mp4")){
         advancedMusicPlayer.playMp4(fileName);
      }
   }
}</code></pre>


<b>Concrete class implementing <code>MediaPlayer</code> interface</b>
<pre><code>public class AudioPlayer implements MediaPlayer {
   MediaAdapter mediaAdapter; 

   @Override
   public void play(String audioType, String fileName) {		

      //inbuilt support to play mp3 music files
      if(audioType.equalsIgnoreCase("mp3")){
         System.out.println("Playing mp3 file. Name: " + fileName);			
      } 
      
      //mediaAdapter is providing support to play other file formats
      else if(audioType.equalsIgnoreCase("vlc") || audioType.equalsIgnoreCase("mp4")){
         mediaAdapter = new MediaAdapter(audioType);
         mediaAdapter.play(audioType, fileName);
      }
      
      else{
         System.out.println("Invalid media. " + audioType + " format not supported");
      }
   }   
}</code></pre>


<b>Play multiple audio files using adaptation of <code>AudioPlayer</code></b>
<pre><code>public class AdapterPatternDemo {
   public static void main(String[] args) {
      AudioPlayer audioPlayer = new AudioPlayer();

      audioPlayer.play("mp3", "beyond the horizon.mp3");
      audioPlayer.play("mp4", "alone.mp4");
      audioPlayer.play("vlc", "far far away.vlc");
   }
}</code></pre>


<b>Output</b>
<pre><code>Playing mp3 file. Name: beyond the horizon.mp3
Playing mp4 file. Name: alone.mp4
Playing vlc file. Name: far far away.vlc</code></pre>
</pre></code>

[<img src="https://cloud.githubusercontent.com/assets/14101008/11768481/3b7d20d6-a18b-11e5-95fe-a422966f4c03.png" width="50" height="50"></img>](https://github.com/hariniiyer/CSCI-5828_Presentation4_Software-Design-Patterns/blob/master/AdapterExample.md)
[<img src="https://cloud.githubusercontent.com/assets/14101008/11768482/3d2d0bbc-a18b-11e5-8766-2e7f5b241782.png" width="50" height="50"></img>](https://github.com/hariniiyer/CSCI-5828_Presentation4_Software-Design-Patterns/blob/master/Bridge.md)


