## Movie Filter

Location in Mac
/Users/carlosinfante/Desktop/coding-projects/winc-academy/frontend-course/MODULE5-ADVANCED JAVASCRIPT/5. Homework_Movie filter/master-movie-filter


Location in Github:

https://github.com/carloscfgos1980/movie-filter/tree/main




* This took me a month to fig it out.

Goals:
- Add elements to the DOM
- Radio buttons.
- A function as argument 
- using sass. Pain in the ass!

# This is a syntetic way to write the function
const filteredMovies = wordInMovie => addMoviesToDom(movies.filter((movie) => movie.title.includes(wordInMovie)));

# more common way to wite the function from above
const filteredMovies = (wordInMovie) => {
    addMoviesToDom(movies.filter((movie) => movie.title.includes(wordInMovie)))

}

# radio buttos. Pain in the ass. Using switch
const handleOnChangeEvent = () => {
    radioBtns.forEach((radiobtn) => {
        radiobtn.addEventListener('change', (event) => {

            switch (event.target.value) {
                case "new-movies":
                    filterLatestMovies();
                    break;
                case "avengers":

                    filteredMovies("Avengers");
                    break;
                case "x-men":

                    filteredMovies("X-Men");
                    break;
                case "princess":

                    filteredMovies("Princess");
                    break;
                case "batman":

                    filteredMovies("Batman");
                    break;
                case "all-movies":

                    addMoviesToDom(movies);
                    break;
            }

        })

    })
}