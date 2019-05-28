# androidBootAnimation
android change boot animation

安卓替换开机动画

1. 制作动画：打开下面链接根据教程制作好动画文件

 https://blog.csdn.net/u010753159/article/details/51356331
 
2. 将制作好的文件添加到压缩文件，压缩文件格式.zip,压缩方式存储，文件名bootanimation

3. 执行替换方法
 public Boolean copyFile(String oldPath, String newPath) { <br> 
        try {<br> 
            int bytesum = 0;<br> 
            int byteread = 0;<br> 
            File oldfile = new File(oldPath);<br> 
            if (oldfile.exists()) { //文件存在时<br> 
                InputStream inStream = new FileInputStream(oldPath); //读入原文件<br> 
                FileOutputStream fs = new FileOutputStream(newPath);<br> 
                byte[] buffer = new byte[8192];<br> 
                while ((byteread = inStream.read(buffer)) != -1) {<br> 
                    bytesum += byteread; //字节数 文件大小
                    fs.write(buffer, 0, byteread);
                }
                inStream.close();
                fs.close();
            }
            return true;
        } catch (Exception e) {
            System.out.println("复制单个文件操作出错");
            File file = new File(requestUrl.upgrade_path
                    + "/bootanimation.zip");
            if (file.exists()) {
                file.delete();
            }
            e.printStackTrace();
            return false;
        }
    }
    
    
     if (copyFile( "your file path", "/data/local/bootanimation.zip")) {
                        BufferedWriter bufferedwriter = null;
                        try {
                            bufferedwriter = new BufferedWriter(new FileWriter("/data/my_fifo"));
                            bufferedwriter.write("replace_bootanimation");
                            bufferedwriter.flush();
                            bufferedwriter.close();
                        } catch (IOException e) {
                            File file_ = new File(requestUrl.upgrade_path
                                    + "/bootanimation.zip");
                            if (file_.exists()) {
                                file_.delete();
                            }
                            initPictureHandler.getInstance(getApplication()).clear();
                            e.printStackTrace();
                        }
                    }
  执行成功后开机重启
                    
