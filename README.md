# nakshd-CriminalFaceDetectionSystem
import java.awt.image.BufferedImage;
import java.io.File;
import javax.imageio.ImageIO;
import java.util.HashMap;
import java.util.Map;

public class CriminalFaceDetectionSystem 
{
private Map<String, BufferedImage> criminalDatabase;
public CriminalFaceDetectionSystem() 
{
criminalDatabase = new HashMap<>();
loadCriminalImages();
}
private void loadCriminalImages() 
{
String[] criminalFiles = {"criminal/criminal1.jpg", "criminal/criminal2.jpg"};
String[] criminalNames = {"Criminal1", "Criminal2"};
for (int i = 0; i < criminalFiles.length; i++) 
{
File file = new File(criminalFiles[i]);
if (file.exists()) 
{
try 
{
criminalDatabase.put(criminalNames[i], ImageIO.read(file));
} 
catch (Exception e) 
{
System.err.println("Error loading image: " + criminalFiles[i]);
e.printStackTrace();
}
} 
else 
{
System.err.println("File not found: " + criminalFiles[i]);
}
}
}
public String detectCriminal(BufferedImage inputImage) 
{
for (Map.Entry<String, BufferedImage> entry : criminalDatabase.entrySet()) 
{
if (matchFaces(inputImage, entry.getValue())) 
{
return entry.getKey();
}
}
return "No match found";
}
private boolean matchFaces(BufferedImage inputImage, BufferedImage criminalImage) 
{
// Implement face matching logic here
return false; 
// Placeholder return
}
public static void main(String[] args) 
{
CriminalFaceDetectionSystem cfdSystem = new CriminalFaceDetectionSystem();
try 
{
BufferedImage inputImage = ImageIO.read(new File("path/to/input.jpg"));
String result = cfdSystem.detectCriminal(inputImage);
System.out.println(result);
} 
catch (Exception e) 
{
System.err.println("Error loading input image.");
e.printStackTrace();
}
}
}

