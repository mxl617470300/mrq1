using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace demo05
{
    struct Poi
    {
        public int x;
        public int y;

        public Poi(int x, int y)
        {
            this.x = x;
            this.y = y;
        }
    }
    class Program
    {
        const int num = 20;
        static string[,] arr = new string[num, num];
        static Poi she;
        static Poi shiwu;
        static Random r = new Random();
        static void Main(string[] args)
        {
            //先给蛇以及食物随机产生一个位置
            she = new Poi(r.Next(1,num-1),r.Next(1,num-1));
            shiwu = new Poi(r.Next(1,num-1),r.Next(1,num-1));


            Show();//打印图形
            while(true)
            {
                ConsoleKeyInfo keyInfo = Console.ReadKey(true);//true:让按下的键不显示
                if (keyInfo.Key == ConsoleKey.W || keyInfo.Key == ConsoleKey.UpArrow)
                {
                    she.x--;
                    if(she.x<=0)
                    {
                        she.x = 1;
                    }
                }
                else if (keyInfo.Key == ConsoleKey.S || keyInfo.Key == ConsoleKey.DownArrow)
                {
                    she.x++;
                    if(she.x>=num-1)
                    {
                        she.x = num - 2;
                    }
                }
                else if (keyInfo.Key == ConsoleKey.A || keyInfo.Key == ConsoleKey.LeftArrow)
                {
                    she.y--;
                    if(she.y<=0)
                    {
                        she.y = 1;
                    }
                }
                else if (keyInfo.Key == ConsoleKey.D || keyInfo.Key == ConsoleKey.RightArrow)
                {
                    she.y++;
                    if(she.y>=num-1)
                    {
                        she.y = num - 2;
                    }
                }
                if(she.x==shiwu.x&&she.y==shiwu.y)
                {
                    shiwu= new Poi(r.Next(1, num - 1), r.Next(1, num - 1));
                }
                //清屏命令
                Console.Clear();
                Show();
            }
            

            //if(keyInfo.KeyChar=='W'||keyInfo.KeyChar=='w')
            //{

            //}



            Console.ReadKey();
        }
        static void Show()
        {
            //给二维数组赋值
            for (int i = 0; i < num; i++)
            {
                for (int j = 0; j < num; j++)
                {
                    if(i==0||i==num-1||j==0||j==num-1)
                    {
                        arr[i,j] = "■";
                    }
                    else
                    {
                        arr[i, j] = "  ";
                    }
                }
            }
            arr[she.x, she.y] = "●";
            arr[shiwu.x, shiwu.y] = "◆";
            //输出二维数组
            for (int i = 0; i < num; i++)
            {
                for (int j = 0; j < num; j++)
                {
                    Console.Write(arr[i,j]);
                }
                Console.WriteLine();
            }
        }
    }
}
