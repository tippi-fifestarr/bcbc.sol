# bcbc.sol
copy paste from remix

///@notice: attempting to use most recent 
///@concept: let users create a workout
//https://cryptomarketpool.com/deploy-a-smart-contract-to-the-polygon-network/
//
pragma solidity ^0.8.4;

///@dev creating the first contract, capable of 
contract workoutFactory {
    //contract begins with allocating memory and variables
    //keep track of all created workouts
    address[] public deployedWorkouts;
    //map the addresses to name
    mapping(address => string) workoutAddress2Name;
    //keep track of how many videos (for looping?)
    uint public videoCount = 0;
    //keep track of the videos array as a map of Video structs
    mapping(uint => Video) public videos;
    //struct of video Data
    struct Video {
        uint id;
        string hash;
        string title;
        address creator;
    }
    //emitable event 
    event VideoUploaded(
        uint id,
        string hash,
        string title,
        address author
    );
    
    //main function of factory is to "mint" workouts
    //first draft just takes _name, possibly add more variables
    function createWorkout(string memory _name) public {
        //creating a new Workout Contract!
        address newWorkout = new Workout(msg.sender, _name);
        
        //add the address of the new workout to deployedWorkouts
        deployedWorkouts.push(newWorkout);
        
        //assign the "name" string to the mapping (note: this may be dumb)
        workoutAddress2Name[newWorkout] = _name;
    }
    
    //function to return all the workouts at once (for ease of display)
    function getDeployedWorkouts() public view returns (address[] memory) {
        return deployedWorkouts;
    }
    
    //i'm thinking to move all the video stuff to the Workout contract
    function uploadVideo(string memory _videoHash, string memory _title) public {
    // Make sure the video hash exists
    require(bytes(_videoHash).length > 0);
    // Make sure video title exists
    require(bytes(_title).length > 0);
    // Make sure uploader address exists
    require(msg.sender!=address(0));

    // Increment video id
    videoCount ++;

    // Add video to the contract
    videos[videoCount] = Video(videoCount, _videoHash, _title, msg.sender);
    // Trigger an event
    emit VideoUploaded(videoCount, _videoHash, _title, msg.sender);
  }

    
    
    //thats it for the MVP of factory i think.
}

//this is the code for the newly deployedWorkout
contract Workout {
    //what memory this needs...
    
    //first datastructure to hold the video metadata?
    // struct Metadata {
    //     string description; //allow workout creator to write something
    //     address creator; //possibly redundant
    //     uint8 approvalCount; //how many validations
    //     uint8 killCount; //how many X (kills)
    //     mapping(address => bool) addressApproved; //prevent double voting
    //     bool isDead; //allow a video to be "killed" by enough X's
    // }
    
//on construction function create video/metadata
    function Workout(string title, address creator,  )
    
    
/////ahhhhhh freakout and start again>!

    
}
