### AduioManager

# 1、获得AudioManager对象实例
AudioManager am = (AudioManager)context.getSystemService(Context.AUDIO_SERVICE);
相关方法详解



3.1.

方法：adjustVolume(int direction, int flags) 

作用：控制手机音量,调大或者调小一个单位,根据第一个参数进行判断 。

参数：AudioManager.ADJUST_LOWER,可调小一个单位; AudioManager.ADJUST_RAISE,可调大一个单位



3.2.

方法：adjustStreamVolume(int streamType, int direction, int flags)： 

作用：同上,不过可以选择调节的声音类型 

参数1：streamType参数,指定声音类型,有下述几种声音类型: 

STREAM_ALARM：手机闹铃 STREAM_MUSIC：手机音乐 

STREAM_RING：电话铃声 STREAM_SYSTEAM：手机系统 

STREAM_DTMF：音调 STREAM_NOTIFICATION：系统提示 

STREAM_VOICE_CALL:语音电话 

参数2：上面那个一样,调大或调小音量的。

参数3：可选的标志位,比如AudioManager.FLAG_SHOW_UI,显示进度条,AudioManager.PLAY_SOUND:播放声音。



3.3.

方法：setStreamVolume(int streamType, int index, intflags)

作用：直接设置音量大小。



3.4.

方法：getMode( )

作用：返回当前的音频模式。



3.5.

方法：setMode( )

作用：设置声音模式 。

返回值：有下述几种模式: 
MODE_NORMAL(普通), MODE_RINGTONE(铃声)

MODE_IN_CALL(打电话)，MODE_IN_COMMUNICATION(通话)



3.6.

方法：getRingerMode( )

作用：返回当前的铃声模式。



3.7.

方法：setRingerMode(int streamType)

作用：设置铃声模式 。

返回值：有下述几种模式: 

如RINGER_MODE_NORMAL（普通）

RINGER_MODE_SILENT（静音）

RINGER_MODE_VIBRATE（震动）



3.8.

方法：getStreamVolume(int streamType)

作用：获得手机的当前音量,最大值为7,最小值为0,当设置为0的时候,会自动调整为震动模式



3.9.

方法：getStreamMaxVolume(int streamType)

作用：获得手机某个声音类型的最大音量值。



3.10.

方法：setStreamMute(int streamType,boolean state)

作用：将手机某个声音类型设置为静音。



3.11.

方法：setSpeakerphoneOn(boolean on)

作用：设置是否打开扩音器。



3.12.

方法：setMicrophoneMute(boolean on)

作用：设置是否让麦克风静音。



3.13.

方法：isMicrophoneMute()

作用：判断麦克风是否静音或是否打开。



3.14.

方法：isMusicActive()

作用：判断是否有音乐处于活跃状态。



3.15.

方法：isWiredHeadsetOn()

作用：判断是否插入了耳机。



3.16.

方法：abandonAudioFocus(AudioManager.OnAudioFocusChangeListenerl)

作用：放弃音频的焦点。



3.17.

方法：adjustSuggestedStreamVolume(int,int suggestedStreamType intflags)

作用：调整最相关的流的音量，或者给定的回退流。



3.18.

方法：getParameters(String keys)

作用：给音频硬件设置一个varaible数量的参数值。



3.19.

方法：getVibrateSetting(int vibrateType)

作用：返回是否该用户的振动设置为振动类型。



3.20.

方法：isBluetoothA2dpOn()

作用：检查是否A2DP蓝牙耳机音频路由是打开或关闭。



3.21.

方法：isBluetoothScoAvailableOffCall()

作用：显示当前平台是否支持使用SCO的关闭调用用例。



3.22.

方法：isBluetoothScoOn()

作用：检查通信是否使用蓝牙SCO。



3.23.

方法：loadSoundEffects()

作用：加载声音效果。



3.24.

方法：playSoundEffect((int effectType, float volume)

作用：播放声音效果。



3.25.

方法：egisterMediaButtonEventReceiver(ComponentName eventReceiver) 

作用：注册一个组件MEDIA_BUTTON意图的唯一接收机。



3.26.

方法：requestAudioFocus(AudioManager.OnAudioFocusChangeListener l,int streamType,int durationHint) 

作用：请求音频的焦点。



3.27.

方法：setBluetoothScoOn(boolean on)

作用：要求使用蓝牙SCO耳机进行通讯。



3.28.

方法：startBluetoothSco/stopBluetoothSco()

作用：启动/停止蓝牙SCO音频连接。



3.29.

方法：unloadSoundEffects()
