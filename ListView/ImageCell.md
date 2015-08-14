## Xamarin Forms ListView > ImageCell  ##

Built-in Image cells used in a Xamarin Forms ListView or TableView. 

```
<?xml version="1.0" encoding="utf-8" ?>
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="MyProject.Views.Shops" Title="Local Shops">


<ScrollView>
  <StackLayout>
      <ListView ItemsSource="{Binding ShopsList}">
        <ListView.ItemTemplate>
          <DataTemplate>
            <ImageCell
               Text="{Binding Name}"
               Detail="{Binding LocationDetails"
               ImageSource="{Binding Image}">
            </ImageCell>
          </DataTemplate>
        </ListView.ItemTemplate>
      </ListView>
  </StackLayout>
</ScrollView>
  
</ContentPage>
```

## References

* [http://developer.xamarin.com/api/type/Xamarin.Forms.ImageCell/ ](http://developer.xamarin.com/api/type/Xamarin.Forms.ImageCell/ )
