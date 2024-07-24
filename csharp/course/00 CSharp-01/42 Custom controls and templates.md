Creating custom controls and templates in .NET Core C# with WPF (Windows Presentation Foundation) allows you to tailor the appearance and behavior of UI elements according to your application's requirements. Here's a step-by-step guide on how to implement custom controls and templates:

### 1. Create a Custom Control Class

Start by creating a new class that inherits from an existing WPF control class, such as `Control`, `Button`, `TextBox`, etc. This class will serve as the code-behind for your custom control.

```csharp
using System.Windows;
using System.Windows.Controls;

namespace YourNamespace
{
    public class MyCustomControl : Control
    {
        static MyCustomControl()
        {
            DefaultStyleKeyProperty.OverrideMetadata(typeof(MyCustomControl), new FrameworkPropertyMetadata(typeof(MyCustomControl)));
        }
    }
}
```

### 2. Define the Control Template

Create a control template in XAML to define the visual appearance and layout of your custom control. This template can include various UI elements and visual states to represent different states of the control.

```xml
<!-- Themes\Generic.xaml -->
<ResourceDictionary xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">

    <Style TargetType="{x:Type local:MyCustomControl}">
        <Setter Property="Template">
            <Setter.Value>
                <ControlTemplate TargetType="{x:Type local:MyCustomControl}">
                    <Border Background="{TemplateBinding Background}"
                            BorderBrush="{TemplateBinding BorderBrush}"
                            BorderThickness="{TemplateBinding BorderThickness}">
                        <ContentPresenter HorizontalAlignment="Center"
                                          VerticalAlignment="Center"
                                          Content="{TemplateBinding Content}"/>
                    </Border>
                </ControlTemplate>
            </Setter.Value>
        </Setter>
    </Style>

</ResourceDictionary>
```

### 3. Associate the Control Template with the Custom Control

In the static constructor of your custom control class, override the default style key property to associate your custom control with its control template.

```csharp
static MyCustomControl()
{
    DefaultStyleKeyProperty.OverrideMetadata(typeof(MyCustomControl), new FrameworkPropertyMetadata(typeof(MyCustomControl)));
}
```

### 4. Merge the Resource Dictionary

Ensure that the resource dictionary containing your control template (typically named Generic.xaml) is merged into the application resources.

```xml
<Application.Resources>
    <ResourceDictionary>
        <ResourceDictionary.MergedDictionaries>
            <ResourceDictionary Source="Themes/Generic.xaml"/>
        </ResourceDictionary.MergedDictionaries>
    </ResourceDictionary>
</Application.Resources>
```

### 5. Use the Custom Control in XAML

You can now use your custom control in XAML like any other built-in control, and it will automatically apply the defined control template.

```xml
<Window x:Class="YourNamespace.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="clr-namespace:YourNamespace">
    <Grid>
        <local:MyCustomControl Content="Hello, Custom Control!"/>
    </Grid>
</Window>
```

### Summary

Creating custom controls and templates in .NET Core C# with WPF allows you to build highly customizable user interfaces tailored to your application's needs. By defining the visual appearance and behavior of your controls through control templates, you can achieve a consistent and polished UI design. Let me know if you need further assistance or more examples!