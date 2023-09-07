# Framer-motion

**Framer Motion Overview**
Framer Motion is a popular animation library for React applications. It allows you to create fluid, interactive animations with a straightforward API. Framer Motion is often used to add animations and transitions to user interfaces, providing a smooth and engaging user experience.

<br>

**Inzstallation and Imports**
```sh
npm install framer-motion
```

```js
import { motion } from "framer-motion"
```

<br>

**How to setup a animation**
```js
<motion.div
    initial={{ opacity: 0, x: -100 }}
    animate={{ opacity: 1, x: 0 }}
    exit={{ opacity: 0, x: 100 }}
    transition={{ duration: 1 }}
>
```
- initial: Defines the initial state of the element.
- animate: Specifies the final state of the element after animation.
- exit: Defines the state of the element when it's removed from the DOM.
- transition: Sets the duration and easing for the animation.
- Its also possible to use rotate, scale and backgroundColor for more complex animations

<br>

**Using Ref and Inersection Observer to Trigger Animations**
```js
import { motion, useAnimation } from "framer-motion";
import { useInView } from "react-intersection-observer";

const MyComponent = () => {

    const boxVariants = (delay) => {
        return{
            hidden: {
                x: -200,
                opacity: 0,
            },
            visible: {
                x: 0,
                opacity: 1,
                transition: {
                    duration: 0.8,
                    delay: delay,
                }
            }
        }
    }

    useEffect(() => {
        if(inView) {
            control.start("visible");
        }
    }, [control, inView]);

    const control = useAnimation();
    const [ref, inView] = useInView();

    return(
        <motion.h2
            ref={ref}
            initial="hidden"
            variants={boxVariants(0)}
            animate={control}
            className={`${styles.heroHeadText}  pb-4 font-bold font-ac w-full text-4xl `}
        >
            Hello World!
        </motion.h2>
    );
}
```
- This h2 element will trigger when the element is present on the users screen
- The boxVariants will make the animation start off invisible(opacity: 0) then render inn from the left(x: -200) and become visible(opacity: 1) and the animation will last 0.8 seconds(duration: 0.8).

