## Binding to ListView item tapped property from View Model

#### CutomListView.cs

```
using System.Windows.Input;
using Xamarin.Forms;

namespace MyApp.Controls
{
    public class CutomListView : ListView
    {
        public static BindableProperty ItemClickCommandProperty = BindableProperty.Create<CutomListView, ICommand>(x => x.ItemClickCommand, null);

        public ICommand ItemClickCommand
        {
            get { return (ICommand)GetValue(ItemClickCommandProperty); }
            set { SetValue(ItemClickCommandProperty, value); }
        }

        private void OnItemTapped(object sender, ItemTappedEventArgs e)
        {
            if (e.Item == null || ItemClickCommand == null || !ItemClickCommand.CanExecute(e)) return;
            ItemClickCommand.Execute(e.Item);
            SelectedItem = null;
        }

        public CutomListView()
        {
            ItemTapped += OnItemTapped;
        }


    }
}

```

#### MyListViewPage.xaml 

```
<?xml version="1.0" encoding="utf-8" ?>
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:viewModels="clr-namespace:MyApp.ViewModels;assembly=MyApp"
             xmlns:controls="clr-namespace:MyApp.Controls;assembly=MyApp"
             x:Class="MyApp.Views.ShopsPage" ">

  <ContentPage.BindingContext>
    <viewModels:ShopsViewModel>
    </viewModels:ShopsViewModel>
  </ContentPage.BindingContext>
  
  <ScrollView>
    <StackLayout Padding="0,8,0,8">
      <StackLayout BackgroundColor="White">
        <controls:CutomListView ItemsSource="{Binding ShopsList}"  ItemClickCommand="{Binding ViewShopCommand}"  >
          <ListView.ItemTemplate>
            <DataTemplate>
              <ImageCell
                 Text="{Binding Name}"
                 Detail="{Binding LocationDetails }"
                 ImageSource="{Binding Image}">
              </ImageCell>
            </DataTemplate>
          </ListView.ItemTemplate>
        </controls:CutomListView>
      </StackLayout>
    </StackLayout>
  </ScrollView>
  </ContentPage>
```
