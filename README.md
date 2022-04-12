# PokeMon API

Link to the [PokeAPI Website](https://pokeapi.co/)  
Link to [documentation](https://pokeapi.co/docs/v2)

The API allows for you to gather any and all data related to Pokemon.

Things that can be queryed:
- Specific Pokemon
- Pokemon by types
- Items
- Moves
- Machines
- Locations
- Games
- Evolutions
- Encounters
- Contests
- Berries

Below is code that would recieve JSON information for a given pokemon name and then display it.
~~~
Route::get(/pokemon/{$name}, function($name) {

    $response = Cache::remember("pokemon-name-$name", 60, function () use ($name) {
        return Http::get("https://pokeapi.co/api/v2/pokemon/$name.json")->object();
    });

     return view('api.pokemon', [
        'response' => $response,
    ]);
}
~~~

Below is what the the JSON that would be recieved when querying about the ditto pokemon.


![Ditto Pokemon Query!](./pokemon-json.png)

