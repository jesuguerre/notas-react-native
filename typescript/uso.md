# Usar TypeScript con React Native

La extensión típica de los archivos TypeScript es `.ts`. Podemos seguir
usando esta extensión cuando escribamos funciones o definiciones de tipos,
pero si queremos usar la sintaxis JSX que usa React Native tendremos que
usar archivos `.tsx`.

Aquí tenemos un ejemplo completo de uso de TypeScript que explicaremos con
detenimiento más adelante:

```typescript
interface ButtonProps {
    text?: string,
    action: () => void,
}

interface ButtonState {
    pressed: boolean,
}

export default class CustomButton extends React.Component<ButtonProps, ButtonState> {
    constructor(props: ButtonProps) {
        super(props);
        this.state { pressed: false };
    }

    render() {
        const realText = this.props.text === null ? 'Button' : this.props.title;
        const background = this.state.pressed ? 'gray' : 'lightgreen';

        return (
            <Button
                style={{backgroundColor: background}}
                title={this.props.text}
                onPress={this.onPress}
                disabled={this.state.pressed} />
        );
    }

    onPress () => {
        this.state.action();
        this.setState({pressed: true});
    }
}
```

Las dos primeras interfaces definen los elementos que deberán tener las
propiedades y el estado de `CustomButton`. Estos nos serán de ayuda ya
que el editor nos autocompletará cada uno de los elementos que hagan falta.
Esto funciona tanto dentro de la propia clase, como si estamos importando
nuestro botón y usándolo en otro archivo.