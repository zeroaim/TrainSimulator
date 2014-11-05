//Station is a sprite -> sprite is an object displayed on the screen all sprites have 2D coordinates (x,y)	
public class Station extends Sprite 
{
	//private String feild containing the station name
	private String name; 
	
	//Method to instantiate a Station a.k.a. Constructor 
	public Station(int x, int y, String name) 
	{
		//runs sprite constructor
		super(x, y);
		//instantiates the name field
		setName(name); 
	}
	//method to "mutate"/"modify" the name field
	public boolean setName(String name) 
	{
		//all stations must have a name otherwise method will not "mutate" its field
		if (name!=null)
		{
			//"mutate" field to name
			this.name = name;
			//name field has been "mutated" confirmation
			return true; 
		}
		//name field has not been "mutated" confirmation
		else 
			return false; 
	}
	//public method for other classes to "access" the stations name
	public String getName()
	{
		return name; 
	}

}






import java.awt.*;
import java.awt.event.*;

import javax.swing.*;

import java.util.ArrayList; 

//A Screen follows the Mouse, Action, MouseMotion, and Key Listers interfaces Mouse is also a JPanel
public class Screen extends JPanel implements MouseListener, ActionListener, MouseMotionListener, KeyListener 
{
	//Create a new animation Timer <javax.swing.Timer>
	public Timer aTime = new Timer(0,this); 
	
	//panel background 
	private JPanel panel;
	
	//Create an ArrayList of Stations
	ArrayList<Station> station = new ArrayList<Station>(); 
	
	//Create a statusbar field of JLabel type
	private JLabel statusbar; 
	
	//Screen constructor/instantiate the screen
	public Screen()
	{ 
		//create a dummy station for development purposes
		station.add(new Station(300,300,"RICHARD STATION"));
		//work in progress window bar <not working yet>
		statusbar = new JLabel("TRAIN SIM BETA V1.0"); 
		//add a the statusbar to the top
		add(statusbar,BorderLayout.NORTH);
		//add the MouseListner to the screen
		addMouseListener(this); 
		//start animation Timer
		aTime.start();
	}
	public void paintComponent(Graphics g)
	{
		/*gray background also for refresh <repaint> in essence (i.e.) 
		it refreshes the screen with a new gray background every update
		removing all previously displayed items */
		g.setColor(Color.GRAY);
		g.fillRect(0, 0, 600, 600);
		//draw station <Place enhanced for loop here for outputting all stations
		g.setColor(Color.BLACK);
		g.fillOval(station.get(0).getX(), station.get(0).getY(), 30, 30);
	}
	//Interface methods 
	//MouseListner interface methods 
	@Override
	public void mouseClicked(MouseEvent event) 
	{
		//development purposes <to be removed/replaced> {moves station}
		station.get(0).setX(event.getX()-15); 
		station.get(0).setY(event.getY()-15); 
	}

	@Override
	public void mouseEntered(MouseEvent event) 
	{
		//development purposes <to be removed/replaced>
		statusbar.setText("Mouse Entered");
	}

	@Override
	public void mouseExited(MouseEvent event)
	{
		//development purposes <to be removed/replaced>
		statusbar.setText("Mouse Exited");
	}

	@Override
	public void mousePressed(MouseEvent event) 
	{
		//development purposes <to be removed/replaced>
		statusbar.setText("Mouse Pressed");
	}

	@Override
	public void mouseReleased(MouseEvent event) 
	{
		//development purposes <to be removed/replaced>
		statusbar.setText("Mouse Released");
	}
	
	//MousemotionListner interface methods
	@Override
	public void mouseDragged(MouseEvent event) 
	{
		//development purposes <to be removed/replaced>
		statusbar.setText("Mouse Dragged");
	}

	@Override
	public void mouseMoved(MouseEvent event) 
	{
		//development purposes <to be removed/replaced>
		statusbar.setText("Mouse Moved");
	}
	//ActionListner interface methods 
	@Override
	public void actionPerformed(ActionEvent event) 
	{
		repaint(); 
	}
	//KeyPressed interface methods
	@Override
	public void keyPressed(KeyEvent event) 
	{
		
	}
	@Override
	public void keyReleased(KeyEvent event) 
	{
		
	}
	@Override
	public void keyTyped(KeyEvent event) 
	{
		
	}
}





// GUI object is a JFrame object 
public class GUI extends JFrame 
{
	//instantiate a GUI Object
	public GUI ()
	{	
		//WIP for window bar <not working> 
		super("TRAIN SIM BETA 1.0");
		//WIP Create a new JPanel <not used>
		JPanel mousepanel = new JPanel(); 
		//Create a Screen object
		Screen screen = new Screen();
		//Create a JFrame object
		JFrame application = new JFrame();
		
		//add the screen to the JFrame Object application 
		application.add(screen); 
		//set the JFrame Object application window size to 600x by 600y
		application.setSize(600,600);
		//set the JFrame object to visible 
		application.setVisible(true);
		
		//WIP <not used>
		mousepanel.addMouseMotionListener(screen); 
	}
}


















//run class 
public class Test 
{
	//run method 
	public static void main(String []args)
	{
		//create a GUI
		new GUI(); 
	}
}

































public class Sprite {
	private int x;
	private int y;
	
	public Sprite(int x, int y)
	{
		setX(x); 
		setY(y); 
	}
	public void setX(int x)
	{
		this.x = x; 
	}
	public int getX()
	{
		return x; 
	}
	public void setY(int y)
	{
		this.y = y; 
	}
	public int getY()
	{
		return y; 
	}
}


