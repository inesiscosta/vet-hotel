# Veterinary Hotel Management System

A text-based management system for a hotel that houses animals, written in Java. It tracks species, animals, habitats, trees, keepers, vets and vaccines, simulates the passing of seasons, and works out how satisfied every animal and employee is.

Built with Miguel Raposo for the Object-Oriented Programming course at Instituto Superior Técnico (2024/2025).

## Features

- **Animals:** register them, move them between habitats, and calculate their satisfaction.
- **Employees:** register zookeepers and vets, and assign or remove the habitats or species they look after.
- **Habitats:** register habitats, change their area, set how each habitat influences each species, and plant trees.
- **Vaccines:** register vaccines and vaccinate animals. Vaccinating with the wrong vaccine can harm the animal.
- **Seasons:** advance the season. Trees age, change their leaves and get harder to clean.
- **Search:** animals in a habitat, an animal's medical history, a vet's medical acts, and all wrong vaccinations.
- **Files:** import a hotel from a text file, and save or load the full state.

## Design

The code is split into a UI layer (`hva.app`, one command class per menu option) and a domain model (`hva.core`) that knows nothing about the UI. Seasons use the **State** pattern, trees use **Observer** to react when the season changes, the app uses **Observer** again to track unsaved changes, and the satisfaction formulas sit behind the **Strategy** pattern. The UML class diagram is in [`docs/uml.grupo49.pdf`](docs/uml.grupo49.pdf).

## Import Format

A hotel can be loaded from a text file with one entity per line. The keywords are in Portuguese, as in the assignment:

```
ESPÉCIE|E1|Cão
HABITAT|H1|Aldeia dos Macacos|420
TRATADOR|T1|Rohit Figueiredo|H1
VETERINÁRIO|V1|Ana Silva|E1
VACINA|V1|Tétano|E1
ANIMAL|A1|Bobi|E1|H1
```

## Running

The UI is built on `po-uilib`, the course's own menu library. It isn't open source, so it isn't in this repo. With the jar in `src/lib/`:

```sh
cd src
javac -cp lib/po-uilib.jar:. $(find hva -name "*.java")
java -cp lib/po-uilib.jar:. hva.app.App                          # start empty
java -cp lib/po-uilib.jar:. -Dimport=hotel.import hva.app.App    # start from an import file
```

```
Main Menu
 1 - New File
 2 - Open File
 3 - Save File
 4 - Next Season
 5 - Calculate Global Satisfaction
 6 - Manage Animals
 7 - Manage Employees
 8 - Manage Habitats
 9 - Manage Vaccines
 10 - Search
 0 - Exit
Choose an option:
```

## License

[MIT](LICENSE) © 2025 Inês Costa and Miguel Raposo
