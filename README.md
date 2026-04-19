# STM32 Bare Metal Programming - Learning Series

A comprehensive beginner-friendly collection of **bare metal STM32 programming exercises** designed to teach embedded systems concepts from the ground up. This repository covers essential GPIO operations, timing, interrupts, and hardware interfacing using direct register manipulation.

## 📚 Purpose

This repository serves as a **hands-on learning resource** for understanding:
- **Microcontroller fundamentals** - How to interact directly with hardware registers
- **GPIO programming** - Controlling digital inputs and outputs
- **Timing and delays** - Software and hardware-based timing mechanisms
- **Interrupt handling** - Event-driven programming with external interrupts
- **Peripheral interfacing** - Connecting and controlling external devices like LCDs and buzzers

All examples use **direct register access** (not HAL libraries), allowing you to understand exactly what's happening at the hardware level.

## 🎯 Target Audience

- **Absolute beginners** in embedded systems development
- Students learning microcontroller programming
- Developers transitioning from high-level to low-level programming
- Anyone interested in understanding STM32 microcontroller architecture

## 📖 Topics Covered

### Basic GPIO Operations
1. **[1.LED Blink (Basic GPIO Output).md](1.LED%20Blink%20%28Basic%20GPIO%20Output%29.md)**
   - Fundamental LED blinking using GPIO output
   - Clock enabling and register configuration
   - Basic timing with software delays

2. **[1.1.Multiple LED Blink .md](1.1.Multiple%20LED%20Blink%20.md)**
   - Controlling multiple LEDs simultaneously
   - Working with GPIO pins 12-15 on PORTD
   - Sequential and pattern-based LED control

3. **[2.LED Toggle Using Bitwise.md](2.LED%20Toggle%20Using%20Bitwise.md)**
   - Bitwise operations for GPIO manipulation
   - Toggling pins efficiently
   - Understanding bit manipulation techniques

### Input and Control
4. **[3.Switch Input → LED Control.md](3.Switch%20Input%20%E2%86%92%20LED%20Control.md)**
   - Reading digital input from switches/buttons
   - GPIO input configuration (IDR register)
   - Conditional logic based on sensor input

5. **[4.Software Debouncing.md](4.Software%20Debouncing.md)**
   - Handling switch bounce in software
   - Timing-based debouncing algorithms
   - Improving reliability of digital inputs

### Timing and PWM
6. **[8.Timer-Based LED Blink.md](8.Timer-Based%20LED%20Blink.md)**
   - Using hardware timers instead of software delays
   - Timer configuration and interrupts
   - Precise timing control

7. **[7.Tone Generation.md](7.Tone%20Generation.md)**
   - PWM (Pulse Width Modulation) basics
   - Generating audio tones
   - Frequency and duty cycle control

### Advanced I/O
8. **[5.LED Binary Counter.md](5.LED%20Binary%20Counter.md)**
   - Using multiple LEDs as a binary display
   - Bit shifting and masking techniques
   - Demonstrating number representation in binary

9. **[5.1.binarywithbutton.md](5.1.binarywithbutton.md)**
   - Binary counter controlled by button input
   - Combining input reading with output control
   - State management in embedded systems

### Interrupt Handling
10. **[9.External Interrupt (EXTI).md](9.External%20Interrupt%20%28EXTI%29.md)**
    - Event-driven programming with external interrupts
    - EXTI configuration and interrupt handlers
    - Reactive programming approach vs polling

### Peripheral Interfacing
11. **[6.Buzzer Control (Basic).md](6.Buzzer%20Control%20%28Basic%29.md)**
    - Controlling a buzzer as a simple actuator
    - On/off control and basic patterns

12. **[10.LCD Interfacing (16x2) Don't use I2C Module.md](10.LCD%20Interfacing%20%2816x2%29%20Don%27t%20use%20I2C%20Module.md)**
    - Interfacing a 16x2 character LCD display
    - Direct parallel communication
    - Display initialization and character output

13. **[10.1.4-bit Mode.md](10.1.4-bit%20Mode.md)**
    - LCD interfacing using 4-bit mode
    - Reducing pin requirements while maintaining functionality
    - Data transmission optimization

## 🚀 Getting Started

### Prerequisites
- **STM32 Microcontroller** (STM32F4 series recommended for these examples)
- **Development Environment**: STM32CubeIDE, Keil uVision, or similar
- **Basic C Programming Knowledge**
- **Understanding of binary and hexadecimal** numbering systems
- **Hardware Components**: LEDs, resistors, buttons, breadboard, etc.

### How to Use This Repository

1. **Start with the basics** - Begin with LED Blink and progress sequentially
2. **Read the explanations** - Each file contains detailed comments explaining the code
3. **Understand the registers** - Focus on understanding what each register does
4. **Experiment** - Modify the code and observe the changes
5. **Build projects** - Combine concepts to create more complex applications

### Example: LED Blink Workflow

```c
// 1. Enable the clock for GPIO port
AHB1_ENR |= (1 << 3);

// 2. Configure pin as output
GPIOD_MODER |= (1 << 24);

// 3. Toggle the pin in a loop
while (1) {
    GPIOD_ODR |= (1 << 12);  // Set high
    led_delay();
    GPIOD_ODR &= ~(1 << 12); // Set low
    led_delay();
}
```

## 🔧 Key Concepts

### Register-Based Programming
All examples use **direct register access** rather than abstraction layers:
- **Memory-mapped registers** for GPIO configuration
- **Bitwise operations** for precise control
- **Base addresses** from the STM32 datasheet

### GPIO Modes
- **Output (MODER = 01)** - Drive pins high or low
- **Input (MODER = 00)** - Read pin states
- **Alternate Function (MODER = 10)** - Special peripheral functions

### Common Registers Used
| Register | Purpose |
|----------|---------|
| `MODER` | Configure pin mode (input/output) |
| `ODR` | Output Data Register (drive pins) |
| `IDR` | Input Data Register (read pins) |
| `BSRR` | Bit Set/Reset Register (atomic operations) |
| `RCC_AHB1ENR` | Enable clock for GPIO port |

## 📚 Learning Resources

- **STM32 Datasheet** - Reference for memory-mapped addresses and registers
- **[bits2bytes](https://mathi27.github.io/bits2bytes/)** - Excellent hardware learning resource (contributor to this project!)
- **ARM Cortex-M4 Reference Manual** - For ISA and system architecture
- **STM32F4 Discovery Board Documentation** - Hardware-specific details

## 💡 Tips for Success

1. **Start simple** - Master GPIO before moving to advanced peripherals
2. **Use a debugger** - Step through code to understand execution flow
3. **Check datasheets** - Memory addresses and register details are essential
4. **Practice bit manipulation** - It's fundamental to embedded programming
5. **Experiment with timings** - Understand the impact of delays on behavior
6. **Document your learning** - Write notes on what each register does

## 🎓 Learning Progression

```
Basic LED Blinking
    ↓
Multiple LEDs & Patterns
    ↓
Switch Input & Control
    ↓
Debouncing & Reliability
    ↓
Binary Operations & Counters
    ↓
Timers & PWM
    ↓
Interrupts & Event-Driven Programming
    ↓
Peripheral Integration (LCD, Buzzer)
```

## 📋 File Organization

Each `.md` file contains:
- **Circuit Diagram** - Hardware connections needed
- **Code Explanation** - What each register does
- **Complete Working Code** - Ready to compile and run
- **Common Issues** - Troubleshooting tips
- **Variations** - How to adapt for different scenarios

## 🛠️ Tools & Environment

**Recommended IDE**: 
- STM32CubeIDE (free, integrated development environment)
- Keil uVision (professional option)
- Visual Studio Code (with cortex-debug extension)

**Compiler**: ARM GCC (gcc-arm-none-eabi)

**Programmer**: 
- ST-Link V2 (built-in for Discovery boards)
- FTDI USB-to-Serial adapters

## 🤝 Contributing

If you have improvements, corrections, or additional tutorials to add:
1. Fork the repository
2. Create a feature branch
3. Add your improvements with clear explanations
4. Submit a pull request

## 📖 Additional Learning

This repository complements the work done on **[bits2bytes](https://mathi27.github.io/bits2bytes/)**, which provides comprehensive hardware fundamentals knowledge. Together, they form a complete foundation for embedded systems learning.

## ⚠️ Important Notes

- **Hardware-Specific**: These examples are tailored for STM32F4 series. Adjust addresses/pins for other STM32 variants.
- **No HAL Library**: This is intentional to build deep understanding of hardware interaction.
- **Safety**: Be careful with electrical connections to avoid damage.
- **Real Delay Issues**: Software delays are not precise; use timers for critical timing.

## 📝 License

This repository is open for educational use. Please credit the original source when using these examples.

---

**Happy Learning! 🚀**

Start with [1.LED Blink (Basic GPIO Output).md](1.LED%20Blink%20%28Basic%20GPIO%20Output%29.md) and progress through the topics sequentially for the best learning experience.

For questions or clarifications, refer to the STM32 datasheet and ARM Cortex-M4 reference manuals.
