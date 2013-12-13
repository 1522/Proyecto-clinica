using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Text;
using System.Windows.Forms;
using MySql.Data.MySqlClient;

namespace Menu
{
    public partial class FrmDoctores : Form
    {
        public FrmDoctores()
        {
            InitializeComponent();
        }
        
        public String clave;


        private int clv;

        private bool Estado = true;

        public int Clave
        {
            set { clv = value; }
            get { return clv; }
        }
        public bool TipoEstado
        {
            set { Estado = value; }
            get { return Estado; }
        }
        public int estado;
        private void CargaEditar()
        {
            MySqlConnection conexion = new MySqlConnection(Conexion.cad);
            MySqlDataAdapter da = new MySqlDataAdapter("select * from TblDoctores where Clave_Doctores=" + clv, conexion);
            DataSet ds = new DataSet();
            da.Fill(ds);
            this.TxtClave.Text = ds.Tables[0].Rows[0].ItemArray[0].ToString();
            this.TxtNombre.Text = ds.Tables[0].Rows[0].ItemArray[1].ToString();
            this.TxtApPat.Text = ds.Tables[0].Rows[0].ItemArray[2].ToString();
            this.TxtApMat.Text = ds.Tables[0].Rows[0].ItemArray[3].ToString();
            this.TxtDomicilio.Text = ds.Tables[0].Rows[0].ItemArray[4].ToString();
            this.TxtTelefono.Text = ds.Tables[0].Rows[0].ItemArray[5].ToString();
            this.TxtFechaNac.Text = ds.Tables[0].Rows[0].ItemArray[6].ToString();
            this.CmbSexo.Text = ds.Tables[0].Rows[0].ItemArray[7].ToString();
            this.TxtCedula.Text = ds.Tables[0].Rows[0].ItemArray[8].ToString();
            this.CmbEspecialidad.Text = ds.Tables[0].Rows[0].ItemArray[9].ToString();
           
        }
        public void modifica()
        {

            MySqlConnection cnn = new MySqlConnection(Conexion.cad);
            cnn.Open();
            MySqlCommand cmd = new MySqlCommand("UPDATE TblDoctores set Clave_Doctores='" + TxtClave.Text + "',Nombre='" + TxtNombre.Text + "',ApellidoPat='" + TxtApPat.Text + "',ApellidoMat='" + TxtApMat.Text + "',Domicilio='" + TxtDomicilio.Text + "',Telefono='" + TxtTelefono.Text + "',Sexo='" + CmbSexo.Text + "',fecha='" + TxtFechaNac.Text + "',Cedula='" + TxtCedula.Text + "',Especialidad='" + CmbEspecialidad.Text + "'  where Clave_Doctores=" + clv, cnn);
            cmd.ExecuteNonQuery();
            cnn.Close();
        }
        public void GuardaNuevo()
        {

            MySqlConnection cnn = new MySqlConnection(Conexion.cad);
            cnn.Open();
            MySqlCommand comando = new MySqlCommand("insert into TblDoctores (Clave_Doctores,Nombre,ApellidoPat,ApellidoMat,Domicilio,Telefono,fecha,Sexo,Cedula,Especialidad)values ('" + TxtClave.Text + "','" + TxtNombre.Text + "','" + TxtApPat.Text + "','" + TxtApMat.Text + "','" + TxtDomicilio.Text + "','" + TxtTelefono.Text + "','" + TxtFechaNac.Text + "','" + CmbSexo.Text + "','" + TxtCedula.Text + "','" + CmbEspecialidad.Text + "')", cnn);
            comando.ExecuteNonQuery();
            cnn.Close();

        }
        private void BtnSalir_Click(object sender, EventArgs e)
        {
            this.Close();
        }

        private void BtnGuardar_Click(object sender, EventArgs e)
        {
            if (TxtNombre.Text == "")
            {
                MessageBox.Show("Falta el Nombre!!", "Doctores", MessageBoxButtons.OK, MessageBoxIcon.Information);
                TxtNombre.Focus();
            }
            else if (TxtApPat.Text == "")
            {
                MessageBox.Show("Falta el Apellido Paterno!!", "Doctores", MessageBoxButtons.OK, MessageBoxIcon.Information);
                TxtApPat.Focus();
            }
            else if (TxtApMat.Text == "")
            {
                MessageBox.Show("Falta el Apellido Materno!!", "Doctores", MessageBoxButtons.OK, MessageBoxIcon.Information);
                TxtApMat.Focus();
            }
            else if (TxtDomicilio.Text == "")
            {
                MessageBox.Show("Falta el Domicilio!!", "Doctores", MessageBoxButtons.OK, MessageBoxIcon.Information);
                TxtDomicilio.Focus();
            }
            else if (TxtTelefono.Text == "")
            {
                MessageBox.Show("Falta el Teléfono!!", "Doctores", MessageBoxButtons.OK, MessageBoxIcon.Information);
                TxtTelefono.Focus();
            }
            else if (TxtFechaNac.Text == "/" || TxtFechaNac.Text == "__/__/____")
            {
                MessageBox.Show("Falta la fecha de Nacimiento!!", "Doctores", MessageBoxButtons.OK, MessageBoxIcon.Information);
                TxtFechaNac.Focus();
            }
            else if (CmbSexo.Text == "")
            {
                MessageBox.Show("Falta elegir el Sexo!!", "Doctores", MessageBoxButtons.OK, MessageBoxIcon.Information);
                CmbSexo.Focus();
            }
            else if (TxtCedula.Text == "")
            {
                MessageBox.Show("Falta la Cédula Profésional", "Doctores", MessageBoxButtons.OK, MessageBoxIcon.Information);
                TxtCedula.Focus();
            }
            else if (CmbEspecialidad.Text == "")
            {
                MessageBox.Show("Falta elegir la Especialidad", "Doctores", MessageBoxButtons.OK, MessageBoxIcon.Information);
                CmbEspecialidad.Focus();
            }
            else
            {
                try
                {
                    if (Estado == true)
                    {
                        GuardaNuevo();
                        MessageBox.Show("Registro Guardado!!", "Doctores", MessageBoxButtons.OK, MessageBoxIcon.Information);
                        BtnGuardar.Enabled = false;
                    }
                    else
                    {
                        modifica();
                        MessageBox.Show("Los Cambios se Guardaron Exitosamente!!", "Doctores", MessageBoxButtons.OK, MessageBoxIcon.Information);
                        BtnGuardar.Enabled = false;
                    }
                }
               		catch
                {
                    MessageBox.Show("Error!!", "Doctores");
                }
            }
        }
             
        
        
        public void AutoClave()
        {
            MySqlConnection cnn = new MySqlConnection(Conexion.cad);
            cnn.Open();
            MySqlDataAdapter da = new MySqlDataAdapter("select Clave_Doctores from TblDoctores ", cnn);
            DataTable dataTable = new DataTable();
            DataSet ds = new DataSet();
            da.Fill(ds);

            string s;

            int t = 0;
            int recordsAffected = da.Fill(dataTable);

            if (recordsAffected > 0)
            {
                foreach (DataRow dr in dataTable.Rows)
                {
                    s = dr[0].ToString();
                    t = Convert.ToInt32(s) + 1;
                }
                TxtClave.Text = t.ToString();

            }
        }

       

        private void FrmDoctores_Load(object sender, EventArgs e)
        {
            AutoClave();
            if (Estado == false)
            {
                CargaEditar();
            }
        }

        private void DtpFechaNac_ValueChanged(object sender, EventArgs e)
        {
            TxtFechaNac.Text = DtpFechaNac.Value.ToShortDateString();
        }

        private void TxtNombre_KeyPress(object sender, KeyPressEventArgs e)
        {
            if (!char.IsControl(e.KeyChar) && !char.IsLetter(e.KeyChar) && !char.IsWhiteSpace(e.KeyChar))
            {
                e.Handled = true;
            }
            base.OnKeyPress(e);

        }

        private void TxtApPat_KeyPress(object sender, KeyPressEventArgs e)
        {
            if (!char.IsControl(e.KeyChar) && !char.IsLetter(e.KeyChar) && !char.IsWhiteSpace(e.KeyChar))
            {
                e.Handled = true;
            }
            base.OnKeyPress(e);
        }

        private void TxtApMat_KeyPress(object sender, KeyPressEventArgs e)
        {
            if (!char.IsControl(e.KeyChar) && !char.IsLetter(e.KeyChar) && !char.IsWhiteSpace(e.KeyChar))
            {
                e.Handled = true;
            }
            base.OnKeyPress(e);
        }

        private void TxtDomicilio_KeyPress(object sender, KeyPressEventArgs e)
        {
            if (!char.IsControl(e.KeyChar) && !char.IsLetterOrDigit(e.KeyChar) && !char.IsWhiteSpace(e.KeyChar))
            {
                e.Handled = true;
            }
            base.OnKeyPress(e);
        }

        private void TxtTelefono_KeyPress(object sender, KeyPressEventArgs e)
        {
            if (!char.IsControl(e.KeyChar) && !char.IsDigit(e.KeyChar))
            {
                e.Handled = true;
            }
            base.OnKeyPress(e);
        }

        private void TxtCedula_KeyPress(object sender, KeyPressEventArgs e)
        {
            if (!char.IsControl(e.KeyChar) && !char.IsLetterOrDigit(e.KeyChar) && !char.IsWhiteSpace(e.KeyChar))
            {
                e.Handled = true;
            }
            base.OnKeyPress(e);
        }

  
     
    }
}
