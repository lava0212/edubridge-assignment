# edubridge-assignment
MENU_PROMPT = "\nEnter 'a' to add a movie, 'l' to see your movies, 'f' to find a movie by title, or 'q' to quit"
movies = []

def add_movie():
    title = input("Enter the movie title: ")
    director = input("Enter the movie director: ")
    year = input("Enter the movie release year: ")
    try:
        year = int(year)
    except ValueError:
        year = None
    movies.append({
        'title': title,
        'director': director,
        'year': year
    })
    
def list_movies():
    for movie in movies:
        print(f"{movie['title']} ({movie['year']}) directed by {movie['director']}")
        
def find_movies(title_input):
    matching_movies = [movie for movie in movies if movie["title"].lower() == title_input.lower()]
    if matching_movies:
        for movie in matching_movies:
            print(f"{movie['title']} ({movie['year']}) directed by {movie['director']}")
    else:
        print("Movie not found.")
        
def user_menu():
    selection = input(MENU_PROMPT)
    while selection != 'q':
        if selection == "a":
            add_movie()
        elif selection == "l":
            list_movies()
        elif selection == "f":
            title = input("Enter movie title to search :")
            find_movies(title)
        else:
            print('Unknown command. Please try again.')
        selection = input(MENU_PROMPT)

if __name__ == "__main__":
    user_menu()
