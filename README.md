<div align="center">
  <h1>InnerSerenity</h1>
  <p>
    <strong>Empowering Minds, Healing Hearts - Your Gateway to Mental Well-being in the Digital Age</strong>
  </p>
  
</div>

InnerSerenity is a decentralized application (DApp) dedicated to promoting mental well-being and providing accessible, confidential, and personalized mental health support. By harnessing the power of blockchain technology, InnerSerenity revolutionizes the mental health landscape, empowering individuals to embark on a journey towards inner peace and serenity.

The DApp begins with the creation of user profiles, where individuals can provide pertinent information about themselves, including their name, age, and gender. These profiles enable mental health professionals to gain valuable insights into their users' backgrounds, helping them tailor their approach and provide personalized support that aligns with the users' unique needs. Professionals, in turn, create comprehensive profiles highlighting their expertise, qualifications, and specialization areas. This allows users to search for professionals based on specific criteria, such as specialization, therapeutic approach, or treatment modality, ensuring they find the most suitable match to address their mental health concerns.

Once users find a professional aligned with their requirements, InnerSerenity facilitates the appointment process, streamlining scheduling and eliminating administrative burdens. Users can request appointments, and professionals can accept or decline based on their availability, ensuring efficient and timely support. InnerSerenity also incorporates a rating system, empowering users to provide feedback and rate the professionals they engage with. This feedback loop promotes accountability, quality improvement, and transparency, benefiting both professionals and users in their mental health journey. The platform also incorporates a unique event ticketing feature, where specialized professionals can organize transformative events and issue ERC1155 tokens to participants. These events foster personal growth, enlightenment, and self-discovery, offering a holistic approach to mental well-being.

# InnerSerenity Code Repositories

# Features
* **User Profiles:** Users can create profiles by providing their name, age, and gender. This information helps professionals understand their users better.
* **Professional Profiles:** Mental health professionals can create profiles by specifying their name and specialization. This feature allows users to search for professionals based on their specific needs.
* **Search Professionals:** Users can search for professionals based on specialization. This functionality helps users find the most suitable professional to address their mental health concerns.
* **Appointment Requests:** Users can request appointments with professionals they are interested in. Professionals have the option to accept or decline these appointment requests based on their availability.
* **Secure Conversations:** Once an appointment is confirmed, users and professionals can engage in secure conversations. The DApp ensures that only the participating users and professionals have access to the conversation.
* **Messaging:** Users and professionals can exchange messages within their conversations. This feature enables effective communication and the sharing of important information related to mental health.
* **Professional Ratings:** After a session, users can rate professionals based on their experience. The rating system helps maintain accountability and provides valuable feedback for professionals to improve their services.
* **Organize Event:** Specialized professionals can organize transformative events and issue ERC1155 tokens to participants, facilitating personal growth, enlightenment, and self-discovery.

# Architecture

## Components

* **Frontend:** frontend of InnerSerenity is responsible for providing users with an intuitive and interactive user interface to access the DApp's features.
* **Sign in with metamask:** InnerSerenity integrates the "Sign in with MetaMask" feature, which allows users to securely authenticate and interact with the DApp using their MetaMask wallet.
* **Backend:** The backend of InnerSerenity handles the server-side operations and serves as the intermediary between the frontend and other external services. It manages user authentication, handles data storage and retrieval and communication with other components.
* **DynamoDB:** DynamoDB is utilized as the database system within InnerSerenity's backend.
* **InnerSerenity Smart contract:** The InnerSerenity Smart Contract is deployed on the Fantom blockchain. It implements the core functionalities and logic of InnerSerenity, including user profile management, professional registration, appointment requests, conversations, and the rating system.
* **Event Ticketing Smart Contract:** The Event Ticketing smart contract facilitates the seamless organization and distribution of event tickets while ensuring transparency and security through the power of blockchain technology. This smart contract allows professionals specializing in various fields to create and issue ERC1155 tokens as event tickets.

# Local Installation

# Usage

* User profiles with personalized information for a comprehensive understanding of user needs.
* Professional profiles highlighting expertise and specialization.
* Search functionality to find professionals based on specific mental health requirements.
* Appointment request system for streamlined scheduling.
* Conversations to ensure secure and confidential communication.
* Rating system to provide feedback and continuous improvement for professionals.
* Participate in transformative events, gain insights, and explore personal growth opportunities.

# Smart Contract Documentation
Our decentralized content sharing dapp uses two different smart contracts to implement two different functionalities:

ERC-1155 TicketFactory contract: This contract allows the creation and management of multiple fungible tokens, each representing a ticket for a specific event. It is suitable for event ticketing as it allows the creation of a large number of identical tickets for an event and easy tracking of their distribution and sale.

ERC-721 ProfileImage contract: This contract allows the creation and management of unique, non-fungible tokens (NFTs), each representing a user's profile image. It is suitable for profile image uploads as it ensures that each user's profile image is unique and cannot be duplicated or replicated. This contract also allows for easy management and tracking of the ownership of each user's profile image.

# ERC-1155 TicketFactory Contract
We use the ERC-1155 TicketFactory contract for event ticketing. This contract allows the creation and management of multiple fungible tokens ( i.e. tokens that are interchangeable with one another ), each representing a ticket for a specific event. This contract is suitable for event ticketing as it allows us to:

Create a large number of identical tickets for an event
Easily track the distribution and sale of tickets
Keep track of the total number of tickets created, the number of tickets sold, the remaining available tickets, event start date and time, and event end date and time.
The TicketFactory contract inherits from ERC1155 and adds the following functionality:
# Structs
1. Ticket Struct

The "Ticket" structure is a key component of our ERC-1155 TicketFactory smart contract. It represents an event hosted by the user and has the following properties:

struct Ticket {
uint256 id;
address creator;
uint256 totalSupply;
uint256 availableSupply;
uint256 price;
uint256 saleStart;
uint256 saleEnd;
string metadataURI;
}
This structure is used to define and keep track of different events and their ticket details within the contract. It allows us to easily create and manage multiple fungible tokens (i.e. tokens that are interchangeable with one another), each representing an event. With the help of this structure, we can keep track of the total number of events created, the number of tickets sold, the remaining available tickets, event start date and time, event end date and time, and other metadata associated with the event.

# Functions
1. Create Ticket Function

The "createTicket" function is a public function defined within our ERC-1155 TicketFactory smart contract. It allows users to create a new event ticket by specifying the following parameters:

"totalSupply": The total number of tickets available for the event.
"price": The price of each ticket in wei.
"saleStart": The start date and time of the ticket sale.
"saleEnd": The end date and time of the ticket sale.
"metadataURI": The URI of the metadata associated with the event.
The function performs various checks to ensure that the inputs provided are valid. For instance, it requires the total supply and price to be greater than 0 and the sale end time to be after the sale start time.

By calling this function, users can create and manage multiple fungible tokens, each representing a ticket for a specific event. This enables efficient tracking of ticket distribution and sale within the contract.

function createTicket( uint256 totalSupply, uint256 price, uint256 saleStart, uint256 saleEnd, string  memory metadataURI ) {}
2. Buy Ticket Function

The "buyTicket" function is another public function defined within our ERC-1155 TicketFactory smart contract. It allows users to purchase event tickets by specifying the following parameters:

"ticketId": The ID of the ticket to be purchased.
"quantity": The number of tickets to be purchased.
By calling this function, users can buy tickets for events in a secure and efficient manner, with the smart contract ensuring that all conditions are met before executing the transaction.

   function buyTicket(uint256 ticketId, uint256 quantity) public payable {}
3. Get Unsold Tickets Function

The "getUnsoldTickets" function is a public view function defined within the ERC-1155 TicketFactory smart contract. It allows users to retrieve an array of all unsold tickets available for purchase, by iterating through all tickets and identifying those that have available supply greater than zero. The function creates a new array to hold the unsold tickets, adds each unsold ticket to the array in reverse order, and returns the array to the user.

function getUnsoldTickets() public view returns (Ticket[] memory) {}

4. Get My Events Function

The "getMyEvents" function is another public view function defined within the ERC-1155 TicketFactory smart contract. It allows users to retrieve an array of all events they have created, by iterating through all tickets and identifying those whose "creator" address matches the caller's address. The function creates a new array to hold the user's events, adds each event to the array in reverse order, and returns the array to the user.

function getMyEvents() public view returns (Ticket[] memory) {}

5. Get My Tickets Function

The "getMyTickets" function is also a public view function defined within the ERC-1155 TicketFactory smart contract. It allows users to retrieve an array of all tickets they have purchased, by iterating through all tickets and identifying those that have been bought by the caller's address. The function creates a new array to hold the user's tickets, adds each ticket to the array in reverse order, and returns the array to the user.

function getMyTickets() public view returns (Ticket[] memory) {}

# Events
1. TicketCreated - emitted when a new event ticket is created.

event TicketCreated( uint256 indexed ticketId, address indexed creator, uint256 totalSupply, uint256 price, uint256 saleStart, uint256 saleEnd, string metadataURI );

This event is emitted when a new event ticket is created, with the following parameters:

"ticketId": The ID of the new ticket.
"creator": The address of the creator of the ticket.
"totalSupply": The total supply of the ticket.
"price": The price of each ticket.
"saleStart": The timestamp of when the ticket sale begins.
"saleEnd": The timestamp of when the ticket sale ends.
"metadataURI": The URI of the metadata associated with the ticket.
2. TicketBought - emitted when a user buys an event ticket.

event TicketBought( uint256 indexed ticketId, address indexed buyer, uint256 quantity, uint256 amount );

This event is emitted when a user buys an event ticket, with the following parameters:

"ticketId": The ID of the purchased ticket.
"buyer": The address of the buyer of the ticket.
"quantity": The number of tickets purchased.
"amount": The total amount paid for the tickets.
ERC-721 ProfileImage Contract
We use the ERC-721 ProfileImage contract for profile image uploads for our users. This contract allows us to create and manage unique, non-fungible tokens (NFTs), each representing a user's profile image. This contract is suitable for profile image uploads as it ensures that:

Each user's profile image is unique and cannot be duplicated or replicated
We can easily manage and track the ownership of each user's profile image.
The ProfileImage contract inherits from ERC721 and adds the following functionality:

# Structs
1. RenderToken struct

struct RenderToken {
uint256 id;
string uri;
string space;
}
Functions
1. Mint NFT Function

The mint function mints a new NFT with a given _uri and assigns it to a given recipient. It returns the ID of the new NFT:

function mint(address recipient, string memory _uri) public returns (uint256) {}
2. Get All Tokens Function

The getAlltoken function returns an array of RenderToken structs representing all the existing NFTs:

function getAlltoken() public view returns (RenderToken[] memory) {}
Events
1. TokenMinted - emitted when a new NFT is minted.

event TokenMinted(uint256 tokenId);
We emit the TokenMinted event whenever a new Profile Image NFT is minted in our smart contract, which includes the newly minted token ID (tokenId). We extract this ID from the blockchain transaction log and store it in Sanity against the user's profile. To ensure additional security, we verify ownership of the NFT by calling the ownerOf(tokenId) function from the ERC-721 standard each time a user's profile page is loaded on the frontend.

# Troubleshooting
**Metamask Login Issue**

If you are unable to sign in with Metamask, please ensure that your Metamask wallet is properly configured and has sufficient funds to pay for the transaction fees. Additionally, ensure that you are signed into Metamask and have granted permission for the dapp to access your wallet.

# Contribution Guidelines
We welcome contributions from anyone who would like to help improve our dapp.

To contribute, please follow the following steps:

1. Fork the repository to your own GitHub account: 
2. Create a new branch from the main branch for your changes.
3. Make your changes and commit them with clear commit messages.
4. Push your changes to your forked repository.
5. Open a pull request to merge your changes into the main branch.

# Team Member
* Hemanth Bugata
* Kushal Sapra
* Hardik Malani
* Suraj Thammi

# Acknowledgements

We are very grateful for these organizations for their contributions to our dapp:
* Fantom community for providing the blockchain network and smart contract ecosystem that InnerSerenity runs on.
* Amazon for providing DynamoDB as the database system within InnerSerenity's backend.
