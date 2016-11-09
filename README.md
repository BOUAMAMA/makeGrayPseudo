# makeGrayPseudo
Learning Java
import edu.duke.*;
import java.io.*;

public class GrayScaleConverter {
	//I started with the image I wanted (inImage)
	public ImageResource makeGray(ImageResource inImage) {
		//I made a blank image of the same size
       ImageResource OutImage = new ImageResource(inImage.getWidth(), inImage.getHeight());
		//for each pixel in outImage
       for (Pixel Outpixel: OutImage.pixels()) {
			//look at the corresponding pixel in inImage
            Pixel inPixel = inImage.getPixel(Outpixel.getX(),Outpixel.getY());
			//compute inPixel's red + inPixel's blue + inPixel's green
			//divide that sum by 3 (call it average)
            int average = inPixel.getRed()+inPixel.getGreen()+inPixel.getBlue() / 3; 
			//set pixel's red to average
            Outpixel.setRed(average);
			//set pixel's green to average
            Outpixel.setGreen(average);
			//set pixel's blue to average
            Outpixel.setBlue(average);

		//outImage is your answer
	}
	    return(OutImage);
}
public void selectAndConvert() {
        DirectoryResource dr = new DirectoryResource();
        for (File f: dr.selectedFiles()){
		ImageResource inImage = new ImageResource(f);
		ImageResource gray = makeGray(inImage);
		gray.draw();
	}
}
}
