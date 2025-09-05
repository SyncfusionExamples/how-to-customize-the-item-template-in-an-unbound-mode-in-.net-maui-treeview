# how-to-customize-the-item-template-in-an-unbound-mode-in-.net-maui-treeview
This repository demonstrates how to customize the item template in unbound mode using the .NET MAUI TreeView (SfTreeView) control. It provides a sample implementation that shows how to use the ItemTemplate and value converters to dynamically style TreeView nodes based on their properties, such as changing text color according to node level.

## Sample
You can customize TreeViewNodes in unbound mode using the ItemTemplate in .NET MAUI TreeView.

Customize the TextColor of the TreeViewNode by using a converter applied to the elements loaded in the ItemTemplate.

### XAML
```xaml
<ContentPage.Resources>
    <ResourceDictionary>
        <local:TextColorConverter x:Key="textColorConverter"/>
    </ResourceDictionary>
</ContentPage.Resources>

<Grid>
    <syncfusion:SfTreeView x:Name="treeView" ItemHeight="25">
        <syncfusion:SfTreeView.ItemTemplate>
            <DataTemplate>
                <Grid>
                    <Label Text="{Binding Content}" TextColor="{Binding Level, Converter={StaticResource textColorConverter}}" VerticalOptions="Center"/>
                </Grid>
            </DataTemplate>
        </syncfusion:SfTreeView.ItemTemplate>

        <syncfusion:SfTreeView.Nodes>
            <treeviewengine:TreeViewNode Content="Australia" IsExpanded="True">
                <treeviewengine:TreeViewNode.ChildNodes>
                    <treeviewengine:TreeViewNode Content="New South Wales">
                        <treeviewengine:TreeViewNode.ChildNodes>
                            <treeviewengine:TreeViewNode Content="Sydney"/>
                            <treeviewengine:TreeViewNode Content="Canberra"/>
                            <treeviewengine:TreeViewNode Content="Newcastle–Maitland"/>
                        </treeviewengine:TreeViewNode.ChildNodes>
                    </treeviewengine:TreeViewNode>
                    <treeviewengine:TreeViewNode Content="Victoria">
                        <treeviewengine:TreeViewNode.ChildNodes>
                            <treeviewengine:TreeViewNode Content="Melbourne"/>
                        </treeviewengine:TreeViewNode.ChildNodes>
                    </treeviewengine:TreeViewNode>
                </treeviewengine:TreeViewNode.ChildNodes>
            </treeviewengine:TreeViewNode>
        </syncfusion:SfTreeView.Nodes>
    </syncfusion:SfTreeView>
</Grid>
```

### Converter
```csharp
public class TextColorConverter : IValueConverter
{
    public object? Convert(object? value, Type targetType, object? parameter, CultureInfo culture)
    {
        var level = (int)value;
        if (level == 0) return Colors.Red;
        else if (level == 1) return Colors.Blue;
        else return Colors.Green;
    }

    public object? ConvertBack(object? value, Type targetType, object? parameter, CultureInfo culture)
    {
        throw new NotImplementedException();
    }
}
```

## Requirements to run the demo

To run the demo, refer to [System Requirements for .NET MAUI](https://help.syncfusion.com/maui/system-requirements).

## Troubleshooting:
### Path too long exception

If you are facing path too long exception when building this example project, close Visual Studio and rename the repository to short and build the project.

## License

Syncfusion® has no liability for any damage or consequence that may arise from using or viewing the samples. The samples are for demonstrative purposes. If you choose to use or access the samples, you agree to not hold Syncfusion® liable, in any form, for any damage related to use, for accessing, or viewing the samples. By accessing, viewing, or seeing the samples, you acknowledge and agree Syncfusion®'s samples will not allow you seek injunctive relief in any form for any claim related to the sample. If you do not agree to this, do not view, access, utilize, or otherwise do anything with Syncfusion®'s samples.