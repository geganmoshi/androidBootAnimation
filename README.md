# androidBootAnimation
android change boot animation

安卓替换开机动画

1. 制作动画：打开下面链接根据教程制作好动画文件

 https://blog.csdn.net/u010753159/article/details/51356331
 
2. 将制作好的文件添加到压缩文件，压缩文件格式.zip,压缩方式存储，文件名bootanimation

3. 执行替换方法<br> 
 public Boolean copyFile(String oldPath, String newPath) { <br> 
        >>try {<br> 
            >>>>int bytesum = 0;<br> 
            >>>>int byteread = 0;<br> 
            >>>>File oldfile = new File(oldPath);<br> 
            >>>>if (oldfile.exists()) { //文件存在时<br> 
                >>>>InputStream inStream = new FileInputStream(oldPath); //读入原文件<br> 
                FileOutputStream fs = new FileOutputStream(newPath);<br> 
                byte[] buffer = new byte[8192];<br> 
                while ((byteread = inStream.read(buffer)) != -1) {<br> 
                    bytesum += byteread; //字节数 文件大小<br> 
                    fs.write(buffer, 0, byteread);<br> 
                }<br> 
                inStream.close();<br> 
                fs.close();<br> 
            }<br> 
            return true;<br> 
        } catch (Exception e) {<br> 
            System.out.println("复制单个文件操作出错");<br> 
            File file = new File(requestUrl.upgrade_path<br> 
                    + "/bootanimation.zip");<br> 
            if (file.exists()) {<br> 
                file.delete();<br> 
            }<br> 
            e.printStackTrace();<br> 
            return false;<br> 
        }<br> 
    }<br> 
    
    
     if (copyFile( "your file path", "/data/local/bootanimation.zip")) {<br> 
                        BufferedWriter bufferedwriter = null;<br> 
                        try {
                            bufferedwriter = new BufferedWriter(new FileWriter("/data/my_fifo"));<br> 
                            bufferedwriter.write("replace_bootanimation");<br> 
                            bufferedwriter.flush();<br> 
                            bufferedwriter.close();<br> 
                        } catch (IOException e) {<br> 
                            File file_ = new File(requestUrl.upgrade_path<br> 
                                    + "/bootanimation.zip");<br> 
                            if (file_.exists()) {<br> 
                                file_.delete();<br> 
                            }<br> 
                            initPictureHandler.getInstance(getApplication()).clear();<br> 
                            e.printStackTrace();<br> 
                        }<br> 
                    }<br> 
  执行成功后开机重启
                    
