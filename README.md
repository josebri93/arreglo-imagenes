    # arreglo-imagenes
    # Explode

La idea es tener una lista de imagenes que vayan cambiando en forma random segun ocurra un evento mousePressed

    PImage [] images = new PImage[4];       // The source image
    PImage imageI;
    int cellsize = 2; // Dimensions of each cell in the grid
    int columns, rows;   // Number of columns and rows in our system

    void setup() {
      size(640, 360, P3D); 
      images[0] = loadImage("image0.jpg");
      images[1] = loadImage("image1.jpg");
      images[2] = loadImage("image2.jpg");
      images[3] = loadImage("image3.jpg");
      //img = loadImage("eames.jpg");  // Load the image

      columns = imageI.width / cellsize;  // Calculate # of columns
      rows = imageI.height / cellsize;  // Calculate # of rows
      println(images.length);
    }

    void draw() {
      background(0);
      // Begin loop for columns
      for ( int i = 0; i < columns; i++) {
        // Begin loop for rows
        for ( int j = 0; j < rows; j++) {
          int x = i*cellsize + cellsize/2;  // x position
          int y = j*cellsize + cellsize/2;  // y position
          int loc = x + y*imageI.width;  // Pixel array location
          color c = imageI.pixels[loc];  // Grab the color
          // Calculate a z position as a function of mouseX and pixel brightness
          float z = (mouseX / float(width)) * brightness(imageI.pixels[loc]) - 20.0;
          // Translate to the location, set fill and stroke, and draw the rect
          pushMatrix();
          translate(x + 160, y + 100, z);
          fill(c, 204);
          noStroke();
          rectMode(CENTER);
          rect(0, 0, cellsize, cellsize);
          popMatrix();
        }
        }
      }

    void mousePressed() {
      //imageI = images[2];
      //cada vez que apriete boton, salta a una imagen de la lista
      imageI = images[int(random(images.length))];
    }
