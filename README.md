# TypeScript Class Notes

> Comprehensive TypeScript learning materials for AltSchool Africa students

![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)
![Slidev](https://img.shields.io/badge/Slidev-83BD75?style=for-the-badge&logo=slidev&logoColor=white)

## Overview

These interactive slides cover TypeScript fundamentals and advanced concepts, designed to transform you into a proficient TypeScript developer. The materials include hands-on examples, exercises, and real-world applications.

## What You'll Learn

### The Basics
- Static type-checking and type safety
- TypeScript compiler (`tsc`) and configuration
- `tsconfig.json` setup and options
- Strictness settings and best practices

### Everyday Types
- **Primitives**: string, number, boolean, null, undefined, bigint, symbol
- **Special Types**: any, unknown, void, never
- **Arrays & Tuples**: Typed collections and fixed-length arrays
- **Objects**: Inline types, optional properties, and readonly modifiers
- **Functions**: Parameter types, return types, rest parameters, overloading
- **Type Aliases & Interfaces**: When to use each
- **Unions & Intersections**: Combining types
- **Literal Types**: Exact value types
- **Enums**: Named constants
- **Type Assertions**: Type casting with `as`
- **Type Guards**: typeof, in operator, type narrowing

### Advanced Patterns
- **Utility Types**: Pick, Omit, Partial, Required, Readonly, Record
- **Generics**: Creating reusable, type-safe components
- **Generic Constraints**: Limiting type parameters
- **Multiple Type Parameters**: Complex generic patterns
- **Type Manipulation**:
  - `keyof` operator
  - `typeof` operator
  - Indexed access types
  - Conditional types
  - Mapped types
  - Template literal types
- **Advanced Operators**: satisfies, as const, non-null assertion (!)

### Function Signatures
- Callback types and function types
- Callable objects with properties
- Call signatures and constructors
- Type-safe event handlers

## Getting Started

### Prerequisites
- Node.js (v14 or higher)
- npm or yarn
- Basic JavaScript knowledge

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/Oluwasetemi/typescript-class-note.git
   cd typescript-class-note
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Start the development server**
   ```bash
   npm run dev
   ```

4. **Open your browser**
   - Visit http://localhost:3030
   - The slides will auto-reload when you make changes

### Build for Production

Generate a static version of the slides:

```bash
npm run build
```

Export slides to PDF:

```bash
npm run export
```

The PDF will be saved as `ts-note.pdf` in the project directory.

## Slide Structure

The slides are organized in a progressive learning path:

1. **Introduction** - What is TypeScript and why use it?
2. **The Basics** - Compiler, configuration, and fundamental concepts
3. **Everyday Types** - Types you'll use daily
4. **Advanced Patterns** - Complex types and real-world patterns
5. **Function Signatures & Callbacks** - Advanced function typing
6. **Generics Deep Dive** - Creating generic functions with magic-move demonstrations
7. **Enums** - Working with named constants
8. **Practical Exercises** - Hands-on coding challenges

## Features

- **Interactive Code Examples**: Live TypeScript playground with Monaco editor
- **Magic Move Animations**: Smooth transitions showing code evolution
- **Progressive Reveals**: Click-through content for better comprehension
- **Syntax Highlighting**: Powered by Shiki
- **Type Checking**: Twoslash integration for inline type information
- **Downloadable PDF**: Export for offline study
- **Mobile Responsive**: Learn on any device

## How to Use These Materials

### For Students
1. **Follow Along**: Work through the slides in order
2. **Try the Code**: Experiment with the interactive examples
3. **Complete Exercises**: Practice with the coding challenges
4. **Take Notes**: Use presenter mode to see slide notes
5. **Review**: Export to PDF for offline reference

### For Instructors
1. **Presenter Mode**: Press `Alt/Option + P` to enter presenter mode
2. **Drawing Mode**: Press `d` to enable drawing on slides
3. **Navigation**: Use arrow keys or click navigation buttons
4. **Overview**: Press `o` to see all slides at once
5. **Edit Slides**: Modify `slides.md` to customize content

## Project Structure

```
typescript-class-note/
├── slides.md              # Main slide content
├── snippets/              # External code snippets
│   └── external.ts
├── package.json           # Dependencies and scripts
├── tsconfig.json          # TypeScript configuration
└── README.md             # This file
```

## Learning Tips

1. **Practice Regularly**: Code along with the examples
2. **Experiment**: Modify examples to see different outcomes
3. **Use TypeScript Playground**: Test concepts at [typescriptlang.org/play](https://www.typescriptlang.org/play)
4. **Read Error Messages**: TypeScript errors are educational
5. **Build Projects**: Apply concepts in real applications

## Additional Resources

- [TypeScript Official Documentation](https://www.typescriptlang.org/)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/intro.html)
- [TypeScript Deep Dive](https://basarat.gitbook.io/typescript/)
- [Type Challenges](https://github.com/type-challenges/type-challenges)
- [TypeScript Exercises](https://typescript-exercises.github.io/)

## Contributing

Found a typo or want to improve the content? Contributions are welcome!

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/improvement`)
3. Make your changes
4. Commit with clear messages (`git commit -m 'Add improved example for generics'`)
5. Push to your branch (`git push origin feature/improvement`)
6. Open a Pull Request

## Author

**Oluwasetemi Ojo**
- Twitter: [@setemiojo](https://twitter.com/setemiojo)
- GitHub: [@Oluwasetemi](https://github.com/Oluwasetemi)
- Website: [oluwasetemi.dev](https://oluwasetemi.dev)

## About AltSchool Africa

[AltSchool Africa](https://altschoolafrica.com) is on a mission to create world-class developers across Africa through practical, project-based learning.

## License

This project is open source and available for educational purposes.

## Acknowledgments

- Built with [Slidev](https://sli.dev/) - Presentation Slides for Developers
- Powered by [TypeScript](https://www.typescriptlang.org/)
- Thanks to the AltSchool Africa community

---

<div align="center">

**Happy Learning!**

Made with care for AltSchool Africa Students and anyone who wants to learn TypeScript

</div>
