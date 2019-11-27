package game.arpg;

import ch.epfl.cs107.play.game.areagame.Area;
import ch.epfl.cs107.play.game.areagame.AreaGame;
import ch.epfl.cs107.play.game.areagame.actor.Orientation;
import ch.epfl.cs107.play.game.tutosSolution.actor.GhostPlayer;
import ch.epfl.cs107.play.game.tutosSolution.area.tuto2.Ferme;
import ch.epfl.cs107.play.game.tutosSolution.area.tuto2.Village;
import ch.epfl.cs107.play.io.FileSystem;
import ch.epfl.cs107.play.math.DiscreteCoordinates;
import ch.epfl.cs107.play.window.Window;

public class ARPG extends RPG {
	public final static float CAMERA_SCALE_FACTOR = 13.f;
	public final static float STEP = 0.05f;


	private GhostPlayer player;
	private final String[] areas = {"zelda/Ferme", "zelda/Village"};
	private final DiscreteCoordinates[] startingPositions = {new DiscreteCoordinates(2,10), 
															 new DiscreteCoordinates(5,15)};

	private int areaIndex;
	/**
	 * Add all the areas
	 */
	private void createAreas(){

		

	}

	@Override
	public boolean begin(Window window, FileSystem fileSystem) {


		if (super.begin(window, fileSystem)) {

			createAreas();
			areaIndex = 0;
			Area area = setCurrentArea(areas[areaIndex], true);
			player = new GhostPlayer(area, Orientation.DOWN, startingPositions[areaIndex],"ghost.1");
			area.registerActor(player);
			area.setViewCandidate(player);
			return true;
		}
		return false;
	}

	@Override
	public void update(float deltaTime) {
		if(player.isPassingADoor()){
			switchArea();         
			player.resetDoorState();
		}
		super.update(deltaTime);

	}

	@Override
	public void end() {
	}

	@Override
	public String getTitle() {
		return "ZeldIC";
	}

	protected void switchArea() {

		player.leaveArea();

		areaIndex = (areaIndex==0) ? 1 : 0;

		Area currentArea = setCurrentArea(areas[areaIndex], false);
		player.enterArea(currentArea, startingPositions[areaIndex]);

		player.strengthen();
	}

}