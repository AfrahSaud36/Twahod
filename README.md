
<h1 align="center">تواحُد</h1>


## Overview

The تواحُد app is designed specifically to assist children with autism by improving their communication skills and fostering social development. It does this by incorporating interactive digital cards that replace traditional physical cards, making the learning experience more engaging and accessible. The app features voice assistance, which provides audio prompts to help children communicate more effectively. By combining these interactive elements, تواحُد aims to create a supportive environment that encourages children to express themselves and interact with others, ultimately enhancing their social skills and communication abilities.

## Features

- **Interactive Digital Cards:** 
  - Transforms traditional physical cards into engaging digital formats, allowing for a more dynamic learning experience.
  - Includes various categories such as emotions, actions, and daily activities to facilitate diverse communication scenarios.

- **Voice Assistance:** 
  - Offers audio prompts that guide users in navigating the app and using the cards effectively.
  - Helps children practice pronunciation and verbal communication by repeating phrases.

- **Intuitive User Interface:** 
  - Designed with children and caregivers in mind, ensuring that navigation is simple and intuitive.
  - Colorful and engaging visuals to maintain the attention of young users.

- **Customizable Content:** 
  - Caregivers can tailor the card content to meet the unique needs of each child, making it more relevant and effective.
  - Option to add personal images and audio to cards for a more personalized experience.

## Purpose

The primary goal of تواحُد is to create an inclusive environment for children with autism, facilitating better communication and social interaction through an engaging digital platform. By leveraging technology, we aim to make learning and communication more enjoyable and accessible.

## Technologies Used

- **Swift:** The primary programming language for iOS development, enabling smooth and efficient application performance.
- **Xcode:** The integrated development environment used for building, testing, and debugging the application.


## How to Use

- Open the app on your device.
- Explore the interactive cards by tapping on them to navigate through different options.
- Use the voice assistance feature by tapping the audio prompt button for help with communication.


## Code




The destinationView(for option: String) function directs the app to the appropriate view based on the provided option. For example, if the input is "feelings," the function returns the FeelingsView, which takes the user to the feelings page of the app. If the option does not match any case, it defaults to displaying "Unknown View."

```swift

private func destinationView(for option: String) -> some View {
        switch option {
        case "feelings":
            return AnyView(FeelingsView())
        case "hurt":
            return AnyView(HurtView())
        case "needs":
            return AnyView(NeedsView())
        case "food":
            return AnyView(FoodView())
        case "clothes":
            return AnyView(ClothingView())
        case "famliy":
            return AnyView(FamliyView())
        default:
            return AnyView(Text("Unknown View"))
        }
    }
```

The AvatarView struct is a SwiftUI view that enables users to select an avatar from a grid of options. It features a state variable, localSelectedAvatar, to track the currently selected avatar, displayed in a circular frame. Users can tap on any avatar in the scrollable grid to update the selection, with a prompt encouraging them to "اختر شخصيتك!" (Choose your character). This design provides an interactive and customizable character selection experience.



```swift

struct AvatarView: View {
    let items: [(imageName: String, frameColor: Color)] = [
        ("avatar1", Color.lightYellow),
        ("avatar2", Color.lightGreen),
        ("avatar3", Color.lightYellow),
        ("avatar4", Color.lightGreen),
        ("avatar5", Color.lightYellow),
        ("avatar6", Color.lightPurple),
        ("avatar7", Color.lightPurple),
        ("avatar8", Color.lightPurple),
        ("avatar1", Color.lightGreen),
        ("avatar1", Color.lightYellow),
        ("avatar2", Color.lightGreen),
        ("avatar3", Color.lightYellow),
        ("avatar4", Color.lightGreen),
        ("avatar5", Color.lightYellow),
        ("avatar6", Color.lightPurple),
        ("avatar7", Color.lightPurple),
        ("avatar8", Color.lightPurple),
        ("avatar1", Color.lightGreen),
    ]
    
    @State private var localSelectedAvatar: String = "avatar3"
    
    var body: some View {
        NavigationView {
            VStack {
                ZStack {
                    Circle().foregroundColor(Color.lightGrey)
                        .frame(width: 150, height: 150)
                    Image(localSelectedAvatar)  // Use the local state variable for the displayed image
                        .resizable()
                        .scaledToFit()  // Maintain aspect ratio
                        .frame(width: 120, height: 120)
                }
                
                Text("اختر شخصيتك!")
                    .foregroundColor(Color.darkGrey)
                    .font(.largeTitle)
                    .fontWeight(.bold)
                    .padding()
                
                ScrollView {
                    LazyVGrid(
                        columns: [GridItem(.adaptive(minimum: 90))], spacing: 10
                    ) {
                        ForEach(Array(items.enumerated()), id: \.offset) {
                            index, item in
                            AvatarFrame(
                                avatarImg: item.imageName,
                                frameColor: item.frameColor
                            )
                            .onTapGesture {
                                localSelectedAvatar = item.imageName
                            }
                        }
                    }
                    .padding(30)
                }
```



## Acknowledgements

I would like to express my gratitude to the Apple Developer Academy for their support and resources throughout this project. Your guidance has been invaluable in bringing تواحُد to life. Additionally, special thanks to the autism community and caregivers for their insights and feedback, which have greatly influenced the development of this application.


## Functionality Overview 

 - **Avatar Selection:** 
- Users can select a personalized avatar from a variety of options. The AvatarView displays interactive cards representing different avatars, allowing children to choose one that resonates with them.
  - The selected avatar is used throughout the app for a personalized experience.
    
-**User-Friendly Interface:**
- The app employs a simple and intuitive interface with clear navigation. The NavigationView ensures that users can easily move between different sections of the app.
  
-**Dynamic Main View:**
- The MainView showcases a welcoming interface with a greeting and the selected avatar displayed prominently. It provides options for various communication topics, such as feelings, needs, and family, through visually appealing cards.
  
-**Search Functionality:**
- Users can search for specific topics using a text field, making it easy to find relevant content quickly.
-**Interactive Navigation:**
- The app features navigation links that guide users to different views, such as FeelingsView, HurtView, and others. Each option is represented visually, encouraging interaction and exploration.
Visual and Auditory Support:
- The app can be enhanced with voice assistance for each card or option, providing auditory feedback that helps reinforce learning and communication skills.

  
-**Engagement through Tap Gestures:**
- Users can engage with the avatar cards using tap gestures, allowing them to select their favorite avatars interactively.

  
-**Clear Content Presentation:**
- Each communication topic (e.g., feelings, needs) is presented in a structured format, making it easy for users to understand and engage with the content.

  
-**Customization:**
- The app allows for customization of the user experience through avatar selection and the ability to navigate to different content areas based on user choice.

  
-**Visual Design:**
- The app employs visually appealing elements, such as rounded rectangles, circles, and color-coded cards, to make the interface engaging and accessible for children.


