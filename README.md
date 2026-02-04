# How to open links reliably using CellDoubleTapped in .NET MAUI DataGrid?

This sample demonstrates how to open links reliably using CellDoubleTapped event in the Syncfusion [.NET MAUI DataGrid](https://help.syncfusion.com/maui/datagrid/overview) (`SfDataGrid`). It ensures that users can open links consistently when a cell is double‑tapped.

## Xaml
```
    <ContentPage.Content>
        <syncfusion:SfDataGrid x:Name="sfdatagrid" 
                            ItemsSource="{Binding Employees}"
                            CellDoubleTapped="sfdatagrid_CellDoubleTapped"
                            GridLinesVisibility="Both"
                            HeaderGridLinesVisibility="Both"
                            AutoGenerateColumnsMode="None">
            

            <syncfusion:SfDataGrid.Columns>
                <syncfusion:DataGridTextColumn MappingName="Name" HeaderText="User Name" />
                <syncfusion:DataGridTextColumn MappingName="Password" HeaderText="Password" />
                <syncfusion:DataGridTextColumn MappingName="Title" HeaderText="Category" />                

                <syncfusion:DataGridTemplateColumn MappingName="Website" HeaderText="Website">
                    <syncfusion:DataGridTemplateColumn.CellTemplate>
                        <DataTemplate>
                            <Label Text="{Binding Website}"
                                TextColor="Blue"
                                TextDecorations="Underline"
                                LineBreakMode="NoWrap"
                                VerticalOptions="Center" />
                        </DataTemplate>
                    </syncfusion:DataGridTemplateColumn.CellTemplate>
                </syncfusion:DataGridTemplateColumn>
            </syncfusion:SfDataGrid.Columns>

        </syncfusion:SfDataGrid>
    </ContentPage.Content>
```

## Xaml.cs
```
 public partial class MainPage : ContentPage
 {
     public MainPage()
     {
         InitializeComponent();
     }

    private async void sfdatagrid_CellDoubleTapped(object sender, Syncfusion.Maui.DataGrid.DataGridCellDoubleTappedEventArgs e)
    {
        var record = e.RowData as Employee;
        var map = e.Column.MappingName;

        if(record != null && !string.IsNullOrWhiteSpace(record.Website) && map is "Website") 
        {
            await Launcher.OpenAsync(record.Website);
        }
    }     

 }
```

### ScreenShot
<img src="https://support.syncfusion.com/kb/agent/attachment/inline?token=eyJhbGciOiJodHRwOi8vd3d3LnczLm9yZy8yMDAxLzA0L3htbGRzaWctbW9yZSNobWFjLXNoYTI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjU4ODAwIiwib3JnaWQiOiIzIiwiaXNzIjoic3VwcG9ydC5zeW5jZnVzaW9uLmNvbSJ9.2Jb9K0RjLW-siAqnTYv5gFa1QVkgc9HpOifVSwM3EIU" width=800/>

[View sample in GitHub](https://github.com/SyncfusionExamples/How-to-open-links-reliably-using-CellDoubleTapped-in-.NET-MAUI-DataGrid-SfDataGrid.git)

 Take a moment to explore this [documentation](https://help.syncfusion.com/maui/datagrid/overview), where you can find more information about Syncfusion .NET MAUI DataGrid (SfDataGrid) with code examples. Please refer to this [link](https://www.syncfusion.com/maui-controls/maui-datagrid) to learn about the essential features of Syncfusion .NET MAUI DataGrid (SfDataGrid).

### Conclusion
I hope you enjoyed learning about how to open links reliably using CellDoubleTapped in SfDataGrid.

You can refer to our [.NET MAUI DataGrid’s feature tour](https://www.syncfusion.com/maui-controls/maui-datagrid) page to learn about its other groundbreaking feature representations. You can also explore our [.NET MAUI DataGrid Documentation](https://help.syncfusion.com/maui/datagrid/getting-started) to understand how to present and manipulate data. For current customers, you can check out our .NET MAUI components on the [License and Downloads](https://www.syncfusion.com/sales/teamlicense) page. If you are new to Syncfusion, you can try our 30-day [free trial](https://www.syncfusion.com/downloads/maui) to explore our .NET MAUI DataGrid and other .NET MAUI components.

If you have any queries or require clarifications, please let us know in the comments below. You can also contact us through our [support forums](https://www.syncfusion.com/forums),[Direct-Trac](https://support.syncfusion.com/create) or [feedback portal](https://www.syncfusion.com/feedback/maui?control=sfdatagrid), or the feedback portal. We are always happy to assist you!