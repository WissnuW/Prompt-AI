# Prompt-AI

Follow this code : 

    // SPDX-License-Identifier: MIT
    pragma solidity ^0.8.13;
    contract Training {

        struct Project {
            string name;
            address[2] founder;
            bool isActive;
        }
        mapping (uint => Project) public projects;
        uint public countProject; // what is this ?

        event Information (uint projectID, string name, address creator);
        constructor () {
            countProject = 0; // and why declaration code like this ? 
        }

        function addProject (string memory _name, address[2] memory _ceo) public {
            // why address use memory in parameters function ? 
            require (bytes(_name).length > 0, "Invalid name"); // why using bytes? 
            require(_ceo.length == 2, "address ceo must same 2");

            projects[countProject] = Project ({
                name: _name,
                founder: _ceo,
                isActive: true
            });
            emit Information (countProject, _name, msg.sender);
        }
        function checkStatus (uint Projects) public {
            require(Projects < countProject, "Not found");
            Project storage _Saving = projects[countProject];
            require(_Saving.isActive, "Status is not Aktive"); // why declarate _Saving.isActive ???

            _Saving.isActive = false;
        }
        function checkCeo (uint Projects) public view returns (address[2] memory) {
            require (Projects < countProject, "Not availble");
            return projects[Projects].founder;
        }
    }

📌Note :
1. explain how the program flow works from input to output
2. explain how each function interacts with each other in this code.
3. Provide the best method to understand the logic of code like this so I can learn faster.
