<script lang="ts">
    interface SeatGrid {
        [row: number]: {
            [column: number]: string;
        };
    }

    let s: SeatGrid = {
        1: {
            1: "rgb(93, 107, 137)",
            2: "rgb(93, 107, 137)",
            3: "rgb(93, 107, 137)",
            4: "rgb(93, 107, 137)",
        },
        2: {
            1: "rgb(93, 107, 137)",
            2: "rgb(93, 107, 137)",
            3: "rgb(93, 107, 137)",
            4: "rgb(93, 107, 137)",
        },
        3: {
            1: "rgb(93, 107, 137)",
            2: "rgb(93, 107, 137)",
            3: "rgb(93, 107, 137)",
            4: "rgb(93, 107, 137)",
        },
        4: {
            1: "rgb(93, 107, 137)",
            2: "rgb(93, 107, 137)",
            3: "rgb(93, 107, 137)",
            4: "rgb(93, 107, 137)",
        },
        5: {
            1: "rgb(93, 107, 137)",
            2: "rgb(93, 107, 137)",
            3: "rgb(93, 107, 137)",
            4: "rgb(93, 107, 137)",
        },
        6: {
            1: "rgb(93, 107, 137)",
            2: "rgb(93, 107, 137)",
            3: "rgb(93, 107, 137)",
            4: "rgb(93, 107, 137)",
        },
        7: {
            1: "rgb(93, 107, 137)",
            2: "rgb(93, 107, 137)",
            3: "rgb(93, 107, 137)",
            4: "rgb(93, 107, 137)",
        },
        8: {
            1: "rgb(93, 107, 137)",
            2: "rgb(93, 107, 137)",
            3: "rgb(93, 107, 137)",
            4: "rgb(93, 107, 137)",
        },
        9: {
            1: "rgb(93, 107, 137)",
            2: "rgb(93, 107, 137)",
            3: "rgb(93, 107, 137)",
            4: "rgb(93, 107, 137)",
        },
        10: {
            1: "rgb(93, 107, 137)",
            2: "rgb(93, 107, 137)",
            3: "rgb(93, 107, 137)",
            4: "rgb(93, 107, 137)",
        },
        11: {
            1: "rgb(93, 107, 137)",
            2: "rgb(93, 107, 137)",
            3: "rgb(93, 107, 137)",
            4: "rgb(93, 107, 137)",
        },
        12: {
            1: "rgb(93, 107, 137)",
            2: "rgb(93, 107, 137)",
            3: "rgb(93, 107, 137)",
            4: "rgb(93, 107, 137)",
        },
    }

    let people: SeatGrid = {
        1: {
            1: "special name 1",
            2: "special name 2",
            3: "special name 3",
            4: "special name 4",
        },
        2: {
            1: "special name 5",
            2: "special name 6",
            3: "special name 7",
            4: "special name 8",
        },
        3: {
            1: "special name 9",
            2: "special name 10",
            3: "special name 11",
            4: "special name 12",
        },
        4: {
            1: "special name 13",
            2: "special name 14",
            3: "special name 15",
            4: "special name 16",
        },
        5: {
            1: "special name 17",
            2: "special name 18",
            3: "special name 19",
            4: "special name 20",
        },
        6: {
            1: "special name 21",
            2: "special name 22",
            3: "special name 23",
            4: "special name 24",
        },
        7: {
            1: "special name 25",
            2: "special name 26",
            3: "special name 27",
            4: "special name 28",
        },
        8: {
            1: "special name 29",
            2: "special name 30",
            3: "special name 31",
            4: "special name 32",
        },
        9: {
            1: "special name 33",
            2: "special name 34",
            3: "special name 35",
            4: "special name 36",
        },
        10: {
            1: "special name 37",
            2: "special name 38",
            3: "special name 39",
            4: "special name 40",
        },
        11: {
            1: "special name 41",
            2: "special name 42",
            3: "special name 43",
            4: "special name 44",
        },
        12: {
            1: "special name 45",
            2: "special name 46",
            3: "special name 47",
            4: "special name 48",
        },
    }

    let seat_array: [number, number][] = [];

    let duck_text = ""

    function clear() {
        for (let i = 1; i <= 12; i++) {
            for (let j = 1; j <= 4; j++) {
                s[i][j] = "rgb(93, 107, 137)";
            }
        }

        seat_array = []

        duck_text = ""

        for (let i = 1; i <= 12; i++) {
            for (let j = 1; j <= 4; j++) {
                seat_array.push([i, j])
            }
        }
    }

    function selection_change() {
        console.log(selected_option)
        clear();
    }

    let selected_option = "Both";

    selection_change()

    function Select() {
        console.log("Select")
        if (seat_array.length == 0) {
            console.log("end of list")
            clear();
        }

        if (selected_option == "Both") {
            let randomIndex = Math.floor(Math.random() * seat_array.length);
            let randomElement = seat_array[randomIndex];
            console.log(randomElement)
            s[randomElement[0]][randomElement[1]] = "rgb(226, 73, 25)"
            seat_array.splice(randomIndex, 1);

            let person_text = ""
            if (randomElement[1] == 1) {
                person_text = "Author"
            } else if (randomElement[1] == 2) {
                person_text = "Musician"
            } else if (randomElement[1] == 3) {
                person_text = "Actor"
            }else if (randomElement[1] == 4) {
                person_text = "President"
            }

            duck_text = "Group " + randomElement[0] + ", " + person_text + " (Person " + randomElement[1] + "), " + people[randomElement[0]][randomElement[1]] + "!"
        }

        if (selected_option == "Group") {
            let randomIndex = Math.floor(Math.random() * seat_array.length);
            let randomElement = seat_array[randomIndex];
            console.log(randomElement);
            let test_index = 0;
            while (test_index < seat_array.length) {
                if (seat_array[test_index][0] == randomElement[0]) {
                    console.log(seat_array[test_index]);
                    s[seat_array[test_index][0]][seat_array[test_index][1]] = "rgb(226, 73, 25)";
                    seat_array.splice(test_index, 1);
                    // Do not increment test_index here because we need to check the new element at this index
                } else {
                    test_index++;
                }
            }
            duck_text = "Group " + randomElement[0] + "!"
        }

        if (selected_option == "Position") {
            let randomIndex = Math.floor(Math.random() * seat_array.length);
            let randomElement = seat_array[randomIndex];
            console.log(randomElement);
            let test_index = 0;
            while (test_index < seat_array.length) {
                if (seat_array[test_index][1] == randomElement[1]) {
                    console.log(seat_array[test_index]);
                    s[seat_array[test_index][0]][seat_array[test_index][1]] = "rgb(226, 73, 25)";
                    seat_array.splice(test_index, 1);
                    // Do not increment test_index here because we need to check the new element at this index
                } else {
                    test_index++;
                }
            }

            let person_text = ""
            if (randomElement[1] == 1) {
                person_text = "Author"
            } else if (randomElement[1] == 2) {
                person_text = "Musician"
            } else if (randomElement[1] == 3) {
                person_text = "Actor"
            }else if (randomElement[1] == 4) {
                person_text = "President"
            }
            duck_text = person_text + " (Person " + randomElement[1] + ")" + "!"
        }
    }
</script>

<hgroup>
    <h1 style="max-width: fit-content; margin-left: auto; margin-right: auto;"><a data-sveltekit-reload href="/">↩</a> Seat Selector</h1>
    <p style="max-width: fit-content; margin-left: auto; margin-right: auto;">Select seats based on group, position, or both.</p>
</hgroup>

<h2 style="max-width: fit-content; margin-left: auto; margin-right: auto;">Our Lucky Duck is: {duck_text}</h2>

<div style="display: flex;">
    <select style="width: 100%; margin: 20px;" name="select" bind:value={selected_option} on:change={selection_change} required>
        <option selected>Both</option>
        <option>Group</option>
        <option>Position</option>
      </select>
      <button on:click={Select} style="width: 100%; margin: 20px;">Select!</button>
      <button on:click={clear} style="width: 100%; margin: 20px;" class="secondary">Clear</button>
</div>

<article>
    <div style="display: flex; margin-top: 60px; margin-bottom: 60px;">
        <div style="width: 100%;">
            <p style="text-align: center; margin: 0px;">12</p>
            <div style="max-width: fit-content; margin-left: auto; margin-right: auto; width: 5em; height: 2.5; display: flex;">
                <div style="background-color: {s[12][3]}; width: 2.5em; height: 2.5em; border-radius: 10px 0 0 0;"><h1 style="text-align: center;">3</h1></div>
                <div style="background-color: {s[12][4]}; width: 2.5em; height: 2.5em; border-radius: 0 10px 0 0;"><h1 style="text-align: center;">4</h1></div>
            </div>
            <div style="max-width: fit-content; margin-left: auto; margin-right: auto; width: 5em; height: 2.5; display: flex;">
                <div style="background-color: {s[12][2]}; width: 2.5em; height: 2.5em; border-radius: 0 0 0 10px;"><h1 style="text-align: center;">2</h1></div>
                <div style="background-color: {s[12][1]}; width: 2.5em; height: 2.5em; border-radius: 0 0 10px 0;"><h1 style="text-align: center;">1</h1></div>
            </div>
        </div>

        <div style="width: 100%;">
            <p style="text-align: center; margin: 0px;">11</p>
            <div style="max-width: fit-content; margin-left: auto; margin-right: auto; width: 5em; height: 2.5; display: flex;">
                <div style="background-color: {s[11][3]}; width: 2.5em; height: 2.5em; border-radius: 10px 0 0 0;"><h1 style="text-align: center;">3</h1></div>
                <div style="background-color: {s[11][4]}; width: 2.5em; height: 2.5em; border-radius: 0 10px 0 0;"><h1 style="text-align: center;">4</h1></div>
            </div>
            <div style="max-width: fit-content; margin-left: auto; margin-right: auto; width: 5em; height: 2.5; display: flex;">
                <div style="background-color: {s[11][2]}; width: 2.5em; height: 2.5em; border-radius: 0 0 0 10px;"><h1 style="text-align: center;">2</h1></div>
                <div style="background-color: {s[11][1]}; width: 2.5em; height: 2.5em; border-radius: 0 0 10px 0;"><h1 style="text-align: center;">1</h1></div>
            </div>
        </div>

        <div style="width: 100%;">
            <p style="text-align: center; margin: 0px;">10</p>
            <div style="max-width: fit-content; margin-left: auto; margin-right: auto; width: 5em; height: 2.5; display: flex;">
                <div style="background-color: {s[10][3]}; width: 2.5em; height: 2.5em; border-radius: 10px 0 0 0;"><h1 style="text-align: center;">3</h1></div>
                <div style="background-color: {s[10][4]}; width: 2.5em; height: 2.5em; border-radius: 0 10px 0 0;"><h1 style="text-align: center;">4</h1></div>
            </div>
            <div style="max-width: fit-content; margin-left: auto; margin-right: auto; width: 5em; height: 2.5; display: flex;">
                <div style="background-color: {s[10][2]}; width: 2.5em; height: 2.5em; border-radius: 0 0 0 10px;"><h1 style="text-align: center;">2</h1></div>
                <div style="background-color: {s[10][1]}; width: 2.5em; height: 2.5em; border-radius: 0 0 10px 0;"><h1 style="text-align: center;">1</h1></div>
            </div>
        </div>

        <div style="width: 100%;">
            <p style="text-align: center; margin: 0px;">9</p>
            <div style="max-width: fit-content; margin-left: auto; margin-right: auto; width: 5em; height: 2.5; display: flex;">
                <div style="background-color: {s[9][3]}; width: 2.5em; height: 2.5em; border-radius: 10px 0 0 0;"><h1 style="text-align: center;">3</h1></div>
                <div style="background-color: {s[9][4]}; width: 2.5em; height: 2.5em; border-radius: 0 10px 0 0;"><h1 style="text-align: center;">4</h1></div>
            </div>
            <div style="max-width: fit-content; margin-left: auto; margin-right: auto; width: 5em; height: 2.5; display: flex;">
                <div style="background-color: {s[9][2]}; width: 2.5em; height: 2.5em; border-radius: 0 0 0 10px;"><h1 style="text-align: center;">2</h1></div>
                <div style="background-color: {s[9][1]}; width: 2.5em; height: 2.5em; border-radius: 0 0 10px 0;"><h1 style="text-align: center;">1</h1></div>
            </div>
        </div>
    </div>

    <div style="display: flex; margin-top: 60px; margin-bottom: 60px;">
        <div style="width: 100%;">
            <p style="text-align: center; margin: 0px;">5</p>
            <div style="max-width: fit-content; margin-left: auto; margin-right: auto; width: 5em; height: 2.5; display: flex;">
                <div style="background-color: {s[5][3]}; width: 2.5em; height: 2.5em; border-radius: 10px 0 0 0;"><h1 style="text-align: center;">3</h1></div>
                <div style="background-color: {s[5][4]}; width: 2.5em; height: 2.5em; border-radius: 0 10px 0 0;"><h1 style="text-align: center;">4</h1></div>
            </div>
            <div style="max-width: fit-content; margin-left: auto; margin-right: auto; width: 5em; height: 2.5; display: flex;">
                <div style="background-color: {s[5][2]}; width: 2.5em; height: 2.5em; border-radius: 0 0 0 10px;"><h1 style="text-align: center;">2</h1></div>
                <div style="background-color: {s[5][1]}; width: 2.5em; height: 2.5em; border-radius: 0 0 10px 0;"><h1 style="text-align: center;">1</h1></div>
            </div>
        </div>

        <div style="width: 100%;">
            <p style="text-align: center; margin: 0px;">6</p>
            <div style="max-width: fit-content; margin-left: auto; margin-right: auto; width: 5em; height: 2.5; display: flex;">
                <div style="background-color: {s[6][3]}; width: 2.5em; height: 2.5em; border-radius: 10px 0 0 0;"><h1 style="text-align: center;">3</h1></div>
                <div style="background-color: {s[6][4]}; width: 2.5em; height: 2.5em; border-radius: 0 10px 0 0;"><h1 style="text-align: center;">4</h1></div>
            </div>
            <div style="max-width: fit-content; margin-left: auto; margin-right: auto; width: 5em; height: 2.5; display: flex;">
                <div style="background-color: {s[6][2]}; width: 2.5em; height: 2.5em; border-radius: 0 0 0 10px;"><h1 style="text-align: center;">2</h1></div>
                <div style="background-color: {s[6][1]}; width: 2.5em; height: 2.5em; border-radius: 0 0 10px 0;"><h1 style="text-align: center;">1</h1></div>
            </div>
        </div>

        <div style="width: 100%;">
            <p style="text-align: center; margin: 0px;">7</p>
            <div style="max-width: fit-content; margin-left: auto; margin-right: auto; width: 5em; height: 2.5; display: flex;">
                <div style="background-color: {s[7][3]}; width: 2.5em; height: 2.5em; border-radius: 10px 0 0 0;"><h1 style="text-align: center;">3</h1></div>
                <div style="background-color: {s[7][4]}; width: 2.5em; height: 2.5em; border-radius: 0 10px 0 0;"><h1 style="text-align: center;">4</h1></div>
            </div>
            <div style="max-width: fit-content; margin-left: auto; margin-right: auto; width: 5em; height: 2.5; display: flex;">
                <div style="background-color: {s[7][2]}; width: 2.5em; height: 2.5em; border-radius: 0 0 0 10px;"><h1 style="text-align: center;">2</h1></div>
                <div style="background-color: {s[7][1]}; width: 2.5em; height: 2.5em; border-radius: 0 0 10px 0;"><h1 style="text-align: center;">1</h1></div>
            </div>
        </div>

        <div style="width: 100%;">
            <p style="text-align: center; margin: 0px;">8</p>
            <div style="max-width: fit-content; margin-left: auto; margin-right: auto; width: 5em; height: 2.5; display: flex;">
                <div style="background-color: {s[8][3]}; width: 2.5em; height: 2.5em; border-radius: 10px 0 0 0;"><h1 style="text-align: center;">3</h1></div>
                <div style="background-color: {s[8][4]}; width: 2.5em; height: 2.5em; border-radius: 0 10px 0 0;"><h1 style="text-align: center;">4</h1></div>
            </div>
            <div style="max-width: fit-content; margin-left: auto; margin-right: auto; width: 5em; height: 2.5; display: flex;">
                <div style="background-color: {s[8][2]}; width: 2.5em; height: 2.5em; border-radius: 0 0 0 10px;"><h1 style="text-align: center;">2</h1></div>
                <div style="background-color: {s[8][1]}; width: 2.5em; height: 2.5em; border-radius: 0 0 10px 0;"><h1 style="text-align: center;">1</h1></div>
            </div>
        </div>
    </div>

    <div style="display: flex; margin-top: 60px; margin-bottom: 60px;">
        <div style="width: 100%;">
            <p style="text-align: center; margin: 0px;">4</p>
            <div style="max-width: fit-content; margin-left: auto; margin-right: auto; width: 5em; height: 2.5; display: flex;">
                <div style="background-color: {s[4][3]}; width: 2.5em; height: 2.5em; border-radius: 10px 0 0 0;"><h1 style="text-align: center;">3</h1></div>
                <div style="background-color: {s[4][4]}; width: 2.5em; height: 2.5em; border-radius: 0 10px 0 0;"><h1 style="text-align: center;">4</h1></div>
            </div>
            <div style="max-width: fit-content; margin-left: auto; margin-right: auto; width: 5em; height: 2.5; display: flex;">
                <div style="background-color: {s[4][2]}; width: 2.5em; height: 2.5em; border-radius: 0 0 0 10px;"><h1 style="text-align: center;">2</h1></div>
                <div style="background-color: {s[4][1]}; width: 2.5em; height: 2.5em; border-radius: 0 0 10px 0;"><h1 style="text-align: center;">1</h1></div>
            </div>
        </div>

        <div style="width: 100%;">
            <p style="text-align: center; margin: 0px;">3</p>
            <div style="max-width: fit-content; margin-left: auto; margin-right: auto; width: 5em; height: 2.5; display: flex;">
                <div style="background-color: {s[3][3]}; width: 2.5em; height: 2.5em; border-radius: 10px 0 0 0;"><h1 style="text-align: center;">3</h1></div>
                <div style="background-color: {s[3][4]}; width: 2.5em; height: 2.5em; border-radius: 0 10px 0 0;"><h1 style="text-align: center;">4</h1></div>
            </div>
            <div style="max-width: fit-content; margin-left: auto; margin-right: auto; width: 5em; height: 2.5; display: flex;">
                <div style="background-color: {s[3][2]}; width: 2.5em; height: 2.5em; border-radius: 0 0 0 10px;"><h1 style="text-align: center;">2</h1></div>
                <div style="background-color: {s[3][1]}; width: 2.5em; height: 2.5em; border-radius: 0 0 10px 0;"><h1 style="text-align: center;">1</h1></div>
            </div>
        </div>

        <div style="width: 100%;">
            <p style="text-align: center; margin: 0px;">2</p>
            <div style="max-width: fit-content; margin-left: auto; margin-right: auto; width: 5em; height: 2.5; display: flex;">
                <div style="background-color: {s[2][3]}; width: 2.5em; height: 2.5em; border-radius: 10px 0 0 0;"><h1 style="text-align: center;">3</h1></div>
                <div style="background-color: {s[2][4]}; width: 2.5em; height: 2.5em; border-radius: 0 10px 0 0;"><h1 style="text-align: center;">4</h1></div>
            </div>
            <div style="max-width: fit-content; margin-left: auto; margin-right: auto; width: 5em; height: 2.5; display: flex;">
                <div style="background-color: {s[2][2]}; width: 2.5em; height: 2.5em; border-radius: 0 0 0 10px;"><h1 style="text-align: center;">2</h1></div>
                <div style="background-color: {s[2][1]}; width: 2.5em; height: 2.5em; border-radius: 0 0 10px 0;"><h1 style="text-align: center;">1</h1></div>
            </div>
        </div>

        <div style="width: 100%;">
            <p style="text-align: center; margin: 0px;">1</p>
            <div style="max-width: fit-content; margin-left: auto; margin-right: auto; width: 5em; height: 2.5; display: flex;">
                <div style="background-color: {s[1][3]}; width: 2.5em; height: 2.5em; border-radius: 10px 0 0 0;"><h1 style="text-align: center;">3</h1></div>
                <div style="background-color: {s[1][4]}; width: 2.5em; height: 2.5em; border-radius: 0 10px 0 0;"><h1 style="text-align: center;">4</h1></div>
            </div>
            <div style="max-width: fit-content; margin-left: auto; margin-right: auto; width: 5em; height: 2.5; display: flex;">
                <div style="background-color: {s[1][2]}; width: 2.5em; height: 2.5em; border-radius: 0 0 0 10px;"><h1 style="text-align: center;">2</h1></div>
                <div style="background-color: {s[1][1]}; width: 2.5em; height: 2.5em; border-radius: 0 0 10px 0;"><h1 style="text-align: center;">1</h1></div>
            </div>
        </div>
    </div>
</article>
