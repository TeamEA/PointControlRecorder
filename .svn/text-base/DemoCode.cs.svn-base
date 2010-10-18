using System;
using System.Text;
using System.Windows;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Controls;

namespace PointControlRecorder
{
    class CalculateYourLife : Window
    {
        TextBox txtBoxBegin, txtBoxEnd;
        Label lbLifeYears;
        [STAThread]
        public static void Main()
        {
            Application app = new Application();
            app.Run(new CalculateYourLife());
        }
        public CalculateYourLife()
        {            
            Title = "Calculate Your Life";
            SizeToContent = SizeToContent.WidthAndHeight;
            ResizeMode = ResizeMode.CanMinimize;
            //建立一个grid
            Grid grid = new Grid();
            Content = grid;
            //
            //row and column
            for (int i = 0; i < 3; i++)
            {
                RowDefinition rowdf = new RowDefinition();
                rowdf.Height = GridLength.Auto;
                grid.RowDefinitions.Add(rowdf);
            }
            for (int i = 0; i < 2; i++)
            {
                ColumnDefinition coldf = new ColumnDefinition();
                coldf.Width = GridLength.Auto;
                grid.ColumnDefinitions.Add(coldf);
            }

            //第一个label
            Label lbl = new Label();
            lbl.Content = "Begin Data: ";
            grid.Children.Add(lbl);
            Grid.SetRow(lbl, 0);
            Grid.SetColumn(lbl, 0);

            //第一个texbox
            txtBoxBegin = new TextBox();
            txtBoxBegin.Text = new DateTime(1988, 10, 17).ToShortDateString();
            txtBoxBegin.TextChanged += TextBoxOnTextChange;
            grid.Children.Add(txtBoxBegin);
            Grid.SetColumn(txtBoxBegin, 1);
            Grid.SetRow(txtBoxBegin, 0);

            //第二个label
            lbl = new Label();
            lbl.Content = "End Data: ";
            grid.Children.Add(lbl);
            Grid.SetRow(lbl, 1);
            Grid.SetColumn(lbl, 0);

            //第二个Textbox
            txtBoxEnd = new TextBox();
            //txtBoxEnd.Text = new DateTime(1988, 10, 17).ToShortDateString();
            txtBoxEnd.TextChanged += TextBoxOnTextChange;
            grid.Children.Add(txtBoxEnd);
            Grid.SetColumn(txtBoxEnd, 1);
            Grid.SetRow(txtBoxEnd, 1);

            //第三个label
            lbl = new Label();
            lbl.Content = "Life Years: ";
            grid.Children.Add(lbl);
            Grid.SetRow(lbl, 2);
            Grid.SetColumn(lbl, 0);

            //计算结果的label
            lbLifeYears = new Label();
            grid.Children.Add(lbLifeYears);
            Grid.SetRow(lbLifeYears, 2);
            Grid.SetColumn(lbLifeYears, 1);

            //设定边界的margin
            Thickness thick = new Thickness(5);
            grid.Margin = thick;

            foreach (Control ctr in grid.Children)
                ctr.Margin = thick;

            //设定焦点和驱动事件处理器
            txtBoxBegin.Focus();
            txtBoxEnd.Text = DateTime.Now.ToShortDateString();
        }
        void TextBoxOnTextChange(object sender, RoutedEventArgs e)
        {
            DateTime dtBeg, dtEnd;
            if (DateTime.TryParse(txtBoxBegin.Text, out dtBeg) &&
                DateTime.TryParse(txtBoxEnd.Text, out dtEnd))
            {
                int iYears = dtEnd.Year - dtBeg.Year;
                int iMonths = dtEnd.Month - dtBeg.Month;
                int iDays = dtEnd.Day - dtBeg.Day;
                if (iDays < 0)
                {
                    iDays += DateTime.DaysInMonth(dtEnd.Year, 1 + (dtEnd.Month + 10) % 12);
                    iMonths -= 1;
                }
                if (iMonths < 0)
                {
                    iMonths += 12;
                    iYears -= 1;
                }
                lbLifeYears.Content =
                    String.Format("{0} year{1},{2} month{3},{4} day{5}",
                    iYears, iYears == 1 ? "" : "s", iMonths, iMonths == 1 ? "" : "s",
                    iDays, iDays == 1 ? "" : "s");

            }
            else
                lbLifeYears.Content = "";
        }
    }
}