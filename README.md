# Layout-Themen-Input

# Inhaltsverzeichnis
- [Übersicht der Layout WPF-Container](#übersicht-der-layout-wpf-container)
- [Übersicht zu den WPF-Styles](#übersicht-zu-den-wpf-styles)
- [WPF-Triggers: Kurzübersicht](#wpf-triggers)
- [WPF-UserControls](#wpf-usercontrols)

---

## Übersicht der Layout WPF-Container
Zweck: Anordnung und Größe von Steuerelementen in der Benutzeroberfläche steuern.
--
### 1. Canvas
   - Ermöglicht absolute Positionierung von Elementen.
   - **Konkrete Anwendungsbeispiele und Umsetzungen:**
     - Positionierung von Grafikelementen wie Ellipsen, Rechtecken, usw.
   - **Vorteile bei der Verwendung:**
     - Präzise Kontrolle über die Positionierung.

### 2. StackPanel
   - Ordnet Elemente horizontal oder vertikal an.
   - **Konkrete Anwendungsbeispiele und Umsetzungen:**
     - Anordnung von Schaltflächen in einer horizontalen Leiste.
   - **Vorteile bei der Verwendung:**
     - Einfache Strukturierung von Elementen in Reihen oder Spalten.

### 3. WrapPanel
   - Ordnet Elemente in einer Zeile oder Spalte an und "wickelt" sie um.
   - **Konkrete Anwendungsbeispiele und Umsetzungen:**
     - Anordnung von Bildern, die sich bei Platzmangel automatisch umreiht.
   - **Vorteile bei der Verwendung:**
     - Automatisches Umreißen von Elementen.

### 4. DockPanel
   - Dockt Elemente an den Rand des verfügbaren Raums.
   - **Konkrete Anwendungsbeispiele und Umsetzungen:**
     - Positionierung von Steuerelementen an den Rändern einer Anwendung.
   - **Vorteile bei der Verwendung:**
     - Fixierung von Elementen an bestimmten Positionen.

### 5. Grid
   - Ermöglicht die Anordnung von Elementen in Zeilen und Spalten.
   - **Konkrete Anwendungsbeispiele und Umsetzungen:**
     - Erstellung komplexer Layouts mit klaren Zeilen- und Spaltenstrukturen.
   - **Vorteile bei der Verwendung:**
     - Flexibles Rasterlayout.

### 6. UniformGrid
   - Teilt den verfügbaren Raum gleichmäßig auf Zeilen und Spalten auf.
   - **Konkrete Anwendungsbeispiele und Umsetzungen:**
     - Erstellung von gleichmäßigen Rasterlayouts.
   - **Vorteile bei der Verwendung:**
     - Gleichmäßige Verteilung von Elementen.

Vorteile von Layoutcontainern:
--
### 1. Flexibilität:

-Anpassung an verschiedene Bildschirmgrößen und Auflösungen.
### 2. Klare Strukturierung:

-Übersichtliches Design der Benutzeroberfläche.
### 3. Effiziente Organisation:

-Verbesserte Benutzererfahrung durch klare Anordnung.

## Beispiel mit Canvas

```xaml
<Window x:Class="CanvasExample.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="Canvas Example" Height="300" Width="400">
    <Canvas>
        <Ellipse Width="50" Height="50" Fill="Blue" Canvas.Left="50" Canvas.Top="50"/>
        <Rectangle Width="80" Height="30" Fill="Green" Canvas.Left="150" Canvas.Top="100"/>
        <TextBlock Text="Hello, Canvas!" Canvas.Left="50" Canvas.Top="200"/>
    </Canvas>
</Window>
```
# Übersicht zu den WPF-Styles
### 1. Was sind WPF-Styles?
Styles sind eine Möglichkeit, das Erscheinungsbild von WPF-Steuerungselementen (Controls) zu definieren.
Sie enthalten Setzungen für visuelle Eigenschaften wie Schriftart, Farbe, Ausrichtung usw.
### 2. Wie werden Styles definiert?
Styles werden normalerweise im XAML-Code definiert, können aber auch programmatisch in Code-Behind erstellt werden.
Hier ist ein einfaches Beispiel für einen TextBlock-Style:
 ```xaml    
<Window.Resources>
<!-- Definition des TextBlock-Styles -->
<Style x:Key="MyTextStyle" TargetType="TextBlock">
<Setter Property="FontSize" Value="14"/>
<Setter Property="Foreground" Value="Blue"/>
</Style>
</Window.Resources>
    <Grid>
<!-- Verwendung des TextBlocks mit dem definierten Style -->
<TextBlock Text="Hello, WPF!" Style="{StaticResource MyTextStyle}"/>
</Grid>
</Window>
```
 
### 3. Globale Styles:
Styles können global in der App.xaml-Datei definiert werden und stehen dann allen Fenstern und Steuerelementen zur Verfügung.

# WPF-Triggers: Kurzübersicht

WPF-Triggers sind mächtige Werkzeuge zur dynamischen Steuerung von Benutzeroberflächen. Property Triggers reagieren auf Eigenschaftsänderungen, DataTriggers auf Datenbindungen, und Event Triggers auf Ereignisse. In dieser Präsentation entdecken wir, wie sie in der Windows Presentation Foundation eingesetzt werden, um flexible und interaktive Benutzeroberflächen zu gestalten.

---

#### Property Trigger Beispiel:

```xaml
<Window x:Class="MainWindow"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
       Title="MainWindow" Height="350" Width="525">
   <Grid>
       <Button Content="Klick mich">
           <Button.Style>
               <Style TargetType="Button">
                   <Style.Triggers>
                       <Trigger Property="IsMouseOver" Value="True">
                           <Setter Property="Background" Value="LightBlue"/>
                       </Trigger>
                   </Style.Triggers>
               </Style>
           </Button.Style>
       </Button>
   </Grid>
</Window>
```

---

#### WPF DataTrigger Beispiel:

```xaml
<Window x:Class="WpfTutorialSamples.Styles.StyleDataTriggerSample"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      Title="StyleDataTriggerSample" Height="200" Width="200">
   <StackPanel HorizontalAlignment="Center" VerticalAlignment="Center">
       <CheckBox Name="cbSample" Content="Hello, world?" />
       <TextBlock HorizontalAlignment="Center" Margin="0,20,0,0" FontSize="48">
           <TextBlock.Style>
               <Style TargetType="TextBlock">
                   <Setter Property="Text" Value="No" />
                   <Setter Property="Foreground" Value="Red" />
                   <!-- DataTrigger: Ändert den Text und die Textfarbe basierend auf dem Zustand der Checkbox -->
                   <Style.Triggers>
                       <DataTrigger Binding="{Binding ElementName=cbSample, Path=IsChecked}" Value="True">
                           <Setter Property="Text" Value="Yes!" />
                           <Setter Property="Foreground" Value="Green" />
                       </DataTrigger>
                   </Style.Triggers>
               </Style>
           </TextBlock.Style>
       </TextBlock>
   </StackPanel>
</Window>
```

# WPF-UserControls
---
UserControl`s sind wiederverwendbare Container-Elemente, die das Markup und den Code gruppieren.
Es ermöglicht die Erstellung einer benutzerdefinierten Benutzeroberfläche mit spezifischer Funktionalität, die an verschiedenen Stellen oder sogar in verschiedenen Anwendungen verwendet werden kann.

Code Beispiel:
--
```xaml
<Grid>    <TextBlock Text="Name:" VerticalAlignment="Center"/>    <TextBox Text="{Binding UserName}" Margin="10,0,0,0"/></Grid>
 ---
