<p align="center" style="font-size: 80px;">تواحُد</p>


## Overview

The تواحُد app is designed specifically to assist children with autism by improving their communication skills and fostering social development. It does this by incorporating interactive digital cards that replace traditional physical cards, making the learning experience more engaging and accessible.

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


