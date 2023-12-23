# alternate
using System.ComponentModel.DataAnnotations;
using System.Security.Permissions;
using System.Text.RegularExpressions;
using System.Data.SqlClient;
using static System.Windows.Forms.VisualStyles.VisualStyleElement.ListView;

namespace WinFormsApp1
{
    public partial class Form1 : Form
    {
        static bool flag = false;
        bool val2=false;
        public Form1()
        {
            InitializeComponent();
        }

        private void button1_Click(object sender, EventArgs e)
        {
            bool f=email_validation();
            bool f1=false;
            if (f == true) { 
                f1=password_validation();
            
            }
            if (f1==true)
            {
                mobile_validation();
            }
                   }
        public bool email_validation()
        {
            string emailPattern = @"^\w+([-+.']\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*$";
            flag = false;
            while (flag == false)
            {
                if (Regex.IsMatch(textBox3.Text, emailPattern))
                {
                    MessageBox.Show("Email Saved Successfully");
                    flag = true;
                }
                else
                {
                    MessageBox.Show("Please enter a valid email address", "Email Validation", MessageBoxButtons.OK, MessageBoxIcon.Warning);
                    flag = false;
                    break;
                }
            }
            return flag;
        }

        public bool password_validation()
        {
            string password = textBox4.Text.Trim();

            if (password.Length >= 8 &&                  // At least 8 characters
                Regex.IsMatch(password, @"\d") &&       // At least one digit
                Regex.IsMatch(password, @"[A-Za-z]"))   // At least one letter
            {
                MessageBox.Show("Password Saved Successfully");
                return true;
            }
            else
            {
                MessageBox.Show("Please enter a valid password (at least 8 characters, including both letters and numbers)", "Password Validation", MessageBoxButtons.OK, MessageBoxIcon.Warning);
                return false;
            }
        }
        public bool mobile_validation()
        {

            if (textBox2.Text.Length == 10)
            {
                flag = true;
                MessageBox.Show("Mobile Number Saved Successfully");
            }
            else { flag = false;
                MessageBox.Show("Enter 10 digit number");
            }
                
            return flag;
        }

        private void label2_Click(object sender, EventArgs e)
        {

        }

        private void textBox1_TextChanged(object sender, EventArgs e)
        {

        }

        private void button2_Click(object sender, EventArgs e)
        {
            email_validation();
            password_validation();




        }

        private void label1_Click(object sender, EventArgs e)
        {

        }

        private void textBox2_TextChanged(object sender, EventArgs e)
        {

        }

        private void textBox3_TextChanged(object sender, EventArgs e)
        {

        }

        private void textBox4_TextChanged(object sender, EventArgs e)
        {
          //  textBox4.PasswordChar = '*';
        }

        private void label4_Click(object sender, EventArgs e)
        {

        }
    }
}
