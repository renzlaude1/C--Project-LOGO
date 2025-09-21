#include <SFML/Graphics.hpp>
#include <SFML/Window.hpp>
#include <iostream>

int main()
{
    // Create the window
    sf::RenderWindow window(sf::VideoMode(800, 600), "Adventure Graphic");

    // Create a background (solid color)
    sf::RectangleShape background(sf::Vector2f(800, 600));
    background.setFillColor(sf::Color(255, 241, 200));  // Beige color

    // Create a circle to represent the sun
    sf::CircleShape sun(100);  // radius 100
    sun.setFillColor(sf::Color(255, 140, 0));  // Orange color
    sun.setPosition(500, 50);  // Positioning the sun

    // Create trees using rectangles (simplified representation)
    sf::RectangleShape tree1(sf::Vector2f(20, 100));
    tree1.setFillColor(sf::Color(0, 128, 0));  // Green for trees
    tree1.setPosition(100, 350);

    sf::RectangleShape tree2(sf::Vector2f(20, 120));
    tree2.setFillColor(sf::Color(0, 128, 0));
    tree2.setPosition(200, 330);

    // Create text for "Adventure" and "Eat Hike Repeat"
    sf::Font font;
    if (!font.loadFromFile("arial.ttf")) {  // Make sure to have the font file
        std::cout << "Failed to load font!" << std::endl;
        return -1;
    }

    sf::Text text("Adventure", font, 50);
    text.setFillColor(sf::Color(0, 0, 0));  // Black color for text
    text.setPosition(300, 450);

    sf::Text subtitle("Eat Hike Repeat", font, 30);
    subtitle.setFillColor(sf::Color(0, 0, 0));  // Black color for text
    subtitle.setPosition(250, 500);

    // Main render loop
    while (window.isOpen()) {
        // Event processing
        sf::Event event;
        while (window.pollEvent(event)) {
            if (event.type == sf::Event::Closed)
                window.close();
        }

        // Clear the window
        window.clear();

        // Draw background, sun, trees, and text
        window.draw(background);
        window.draw(sun);
        window.draw(tree1);
        window.draw(tree2);
        window.draw(text);
        window.draw(subtitle);

        // Display everything we just drew
        window.display();
    }

    return 0;
}
