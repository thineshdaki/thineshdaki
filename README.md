- 👋 Hi, I’m @thineshdaki
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
thineshdaki/thineshdaki is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using System.Windows.Forms;
using System.Collections;
using System.Diagnostics;
using System.Drawing;
using System.Linq;
using System.Resources;
using System.Runtime.CompilerServices;
using System.Runtime.InteropServices;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using System.Windows.Forms;
using Memory;
using System.IO;
using System.Security.Cryptography;


namespace note_888
{
    internal static class Program
    {


        public partial class Form1 : Form
        {
            public static bool IsAlreadyRunning;

            private string sr;

            public long enumerable = (long)0;

            private int x;
            private string str;

            public Mem MemLib = new Mem();
            public Imps MemLib1 = new Imps();

            private static string string_0;

            private IContainer icontainer_0;




            private Label label1;


            public Form1()
            {




                [DllImport("KERNEL32.DLL")]
                public static extern int Process32First(IntPtr handle, ref ProcessEntry32 pe);

                [DllImport("KERNEL32.DLL")]
                public static extern int Process32Next(IntPtr handle, ref ProcessEntry32 pe);

                private async Task PutTaskDelay(int Time)
                {
                    await Task.Delay(Time);
                }

                [DllImport("KERNEL32.DLL", CharSet = CharSet.None, ExactSpelling = true)]
                public static extern IntPtr CreateToolhelp32Snapshot(uint flags, uint processid);
        public struct ProcessEntry32
            {
                public uint dwSize;

                public uint cntUsage;

                public uint th32ProcessID;

                public IntPtr th32DefaultHeapID;

                public uint th32ModuleID;

                public uint cntThreads;

                public uint th32ParentProcessID;

                public int pcPriClassBase;

                public uint dwFlags;

                [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 260)]

                public string szExeFile;
            }





            private async Task<IntPtr> emuladores1()
            {
                bool flag;
                bool flag1;
                bool flag2;
                bool flag3;
                bool flag4;
                bool flag5;
                str = null;
                string str1 = null;
                string str2 = "HD-Player";
                string str3 = "HD-Player.exe";
                string str4 = "MEmuHeadless";
                string str5 = "aow_exe";
                string str6 = "AndroidProcess.exe";
                string str7 = "LdVBoxHeadless.exe";
                IntPtr zero = IntPtr.Zero;
                uint num = 0;
                IntPtr intPtr = CreateToolhelp32Snapshot(2, 0);

                if ((int)intPtr > 0)
                {
                    ProcessEntry32 processEntry32 = default;
                    processEntry32.dwSize = (uint)Marshal.SizeOf<ProcessEntry32>(processEntry32);
                    for (int i = Process32First(intPtr, ref processEntry32); i == 1; i = Process32Next(intPtr, ref processEntry32))
                    {
                        IntPtr intPtr1 = Marshal.AllocHGlobal((int)processEntry32.dwSize);
                        Marshal.StructureToPtr<ProcessEntry32>(processEntry32, intPtr1, true);
                        ProcessEntry32 structure = (ProcessEntry32)Marshal.PtrToStructure(intPtr1, typeof(ProcessEntry32));
                        Marshal.FreeHGlobal(intPtr1);
                        flag = (!structure.szExeFile.Contains(str2) ? false : structure.cntThreads > num);
                        if (flag)
                        {
                            num = structure.cntThreads;
                            zero = (IntPtr)((ulong)structure.th32ProcessID);
                        }
                        flag1 = (!structure.szExeFile.Contains(str4) ? false : structure.cntThreads > num);
                        if (flag1)
                        {
                            num = structure.cntThreads;
                            zero = (IntPtr)((ulong)structure.th32ProcessID);
                        }
                        flag2 = (!structure.szExeFile.Contains(str5) ? false : structure.cntThreads > num);
                        if (flag2)
                        {
                            num = structure.cntThreads;
                            zero = (IntPtr)((ulong)structure.th32ProcessID);
                        }
                        flag3 = (!structure.szExeFile.Contains(str3) ? false : structure.cntThreads > num);
                        if (flag3)
                        {
                            num = structure.cntThreads;
                            zero = (IntPtr)((ulong)structure.th32ProcessID);
                        }
                        flag4 = (!structure.szExeFile.Contains(str6) ? false : structure.cntThreads > num);
                        if (flag4)
                        {
                            num = structure.cntThreads;
                            zero = (IntPtr)((ulong)structure.th32ProcessID);
                        }
                        flag5 = (!structure.szExeFile.Contains(str7) ? false : structure.cntThreads > num);
                        if (flag5)
                        {
                            num = structure.cntThreads;
                            zero = (IntPtr)((ulong)structure.th32ProcessID);
                        }
                        structure = new ProcessEntry32();
                    }
                    PID.Text = Convert.ToString(zero);
                    await PutTaskDelay(1000);
                    changeMEMORYNOt();
                    processEntry32 = new Form1.ProcessEntry32();


                }

                IntPtr intPtr2 = zero;
                str2 = null;
                str3 = null;
                str4 = null;
                str5 = null;
                str6 = null;
                str7 = null;
                return intPtr2;


            }




 public async void changeMEMORYNOt()
        {

            string str = null;
            Imps.MemoryProtection memoryProtection;
           string str1 = null;
            Imps.MemoryProtection memoryProtection1;
            bool flag = false;
            int num = 1;
            if (Convert.ToInt32(PID.Text) == 0)
            {
                PSPS.ForeColor = Color.Red;
                PSPS.Text = "Error al Conectar.";
            }
            PSPS.ForeColor = Color.Orange;
            PSPS.Text = "Conectado.";
            MemLib.OpenProcess(Convert.ToInt32(PID.Text));
            Thread.Sleep(2000);
            PSPS.ForeColor = Color.Green;
            PSPS.Text = "Aplicando...";
            var enumerable = await MemLib.AoBScan(0, 140737488355327L, "80 37 8F 3C", false, false, "");

            string_0 = "0x" + enumerable.FirstOrDefault().ToString("X");
            MemLib.ChangeProtection(string_0, Imps.MemoryProtection.ReadWrite, out memoryProtection, "");


            foreach (long num2 in enumerable)
            {
                MemLib.WriteMemory(num2.ToString("X"), "bytes", "80 6D F4 00", "", null);
                flag = false;
            }
            if (flag)
            {
                PSPS.Text = "Aplicado Correctamente!";
                PSPS.ForeColor = Color.Purple;
                await PutTaskDelay(500);
            }
            else if (num >= 4)
            {
                PSPS.Text = "Error al aplicar...";
                PSPS.ForeColor = Color.Red;
            }
            else
            {
                PSPS.ForeColor = Color.Red;
                PSPS.Text = "Error Aplique de nuevo...";
                num += 1;
            }
            MemLib.ChangeProtection(string_0, Imps.MemoryProtection.ReadOnly, out memoryProtection1, "");
            MemLib.CloseProcess();

        }


                /// <summary>
                /// The main entry point for the application.
                /// </summary>
                [STAThread]
        static void Main()
        {
            Application.EnableVisualStyles();
            Application.SetCompatibleTextRenderingDefault(false);
            Application.Run(new Form1());
        }
    }
}

