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
    public partial class FrmCitas : Form
    {
        public FrmCitas()
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

        public void GuardaNuevo()
        {

            MySqlConnection cnn = new MySqlConnection(Conexion.cad);
            cnn.Open();                                                  
            MySqlCommand comando = new MySqlCommand("insert into TblCitas (FolioCitas,Clave_Pacientes,Nombre,ApellidoPat,ApellidoMat,Clave_Doctores,Hora,Estatura,Peso,Temperatura,Precion,fecha)values ('" + TxtFolioCitas.Text + "','" + TxtClvPaciente.Text + "','" + TxtNombre.Text + "','" + TxtApPat.Text + "','" + TxtApMat.Text + "','" + CmbDoctor.SelectedValue.ToString() + "','" + TxtHora.Text + "','" + TxtEstatura.Text + "','" + TxtPeso.Text + "','" + TxtTemperatura.Text + "','" + TxtPresion.Text + "','" + TxtFecha.Text + "')", cnn);
            comando.ExecuteNonQuery();
            cnn.Close();

        }
        private void CargaEditar()
        {
            MySqlConnection conexion = new MySqlConnection(Conexion.cad);
            MySqlDataAdapter da = new MySqlDataAdapter("select *from TblCitas where FolioCitas=" + clv, conexion);
            DataSet ds = new DataSet();
            da.Fill(ds);
            BtnBuscarReg.Enabled = false;
            BtnAgregar.Enabled = false;

        
        }
        public void modifica()
        {
            MySqlConnection conexion = new MySqlConnection(Conexion.cad);
            conexion.Open();
            MySqlCommand cmd = new MySqlCommand("update TblCitas set FolioCitas='" + TxtFolioCitas.Text + "',Clave_Pacientes='" + TxtClvPaciente.Text + "',Nombre='" + TxtNombre.Text + "',ApellidoPat='" + TxtApPat.Text + "',ApellidoMat='" + TxtApMat.Text + "',Clave_Doctores='" + CmbDoctor.SelectedValue.ToString() + "',Hora='" + TxtHora.Text + "',Estatura='" + TxtEstatura.Text + "',Peso='" + TxtPeso.Text + "',Temperatura='" + TxtTemperatura.Text + "',Precion='" + TxtPresion.Text + "',fecha='" + TxtFecha.Text + "' where FolioCitas=" + clv, conexion);
            cmd.ExecuteNonQuery();
            conexion.Close();
        }
        private void CargaDoctores()
        {
            MySqlConnection cnn = new MySqlConnection(Conexion.cad);
            MySqlDataAdapter da = new MySqlDataAdapter("select  Clave_Doctores,Nombre from TblDoctores", cnn);
            DataSet ds = new DataSet();
            da.Fill(ds);
            CmbDoctor.DataSource = ds.Tables[0];
            CmbDoctor.DisplayMember = "Nombre";
            CmbDoctor.ValueMember = "Clave_Doctores";
        }

        private void BtnAgregar_Click(object sender, EventArgs e)
        {
            FrmPacientes addpaciente = new FrmPacientes();
            addpaciente.ShowDialog();
        }

        private void BtnSalir_Click(object sender, EventArgs e)
        {
            this.Close();
        }

        private void BtnGuardar_Click(object sender, EventArgs e)
        {
            if (TxtClvPaciente.Text == "")
            {
                MessageBox.Show("Falta la clave del Paciente!!", "Citas", MessageBoxButtons.OK, MessageBoxIcon.Information);
                TxtClvPaciente.Focus();
            }
            if (TxtNombre.Text == "")
            {
                MessageBox.Show("Falta el Nombre!!", "Citas", MessageBoxButtons.OK, MessageBoxIcon.Information);
                TxtNombre.Focus();
            }
            else if (TxtApPat.Text == "")
            {
                MessageBox.Show("Falta el Apellido Paterno!!", "Citas", MessageBoxButtons.OK, MessageBoxIcon.Information);
                TxtApPat.Focus();
            }
            else if (TxtApMat.Text == "")
            {
                MessageBox.Show("Falta el Apellido Materno!!", "Citas", MessageBoxButtons.OK, MessageBoxIcon.Information);
                TxtApMat.Focus();
            }
            else if (CmbDoctor.Text == "")
            {
                MessageBox.Show("Falta elegir el Doctor!!", "Citas", MessageBoxButtons.OK, MessageBoxIcon.Information);
                CmbDoctor.Focus();
            }
            else if (TxtHora.Text == "__:__")
            {
                MessageBox.Show("Falta especificar la Hora!!", "Citas", MessageBoxButtons.OK, MessageBoxIcon.Information);
                TxtHora.Focus();
            }
            else if (TxtEstatura.Text == "")
            {
                MessageBox.Show("Falta la Estatura!!", "Citas", MessageBoxButtons.OK, MessageBoxIcon.Information);
                TxtEstatura.Focus();
            }
            else if (TxtFecha.Text == "/" || TxtFecha.Text == "__/__/____")
            {
                MessageBox.Show("Falta la fecha de la Cita!!", "Citas", MessageBoxButtons.OK, MessageBoxIcon.Information);
                TxtFecha.Focus();
            }
            else if (TxtPeso.Text == "")
            {
                MessageBox.Show("Falta el Peso!!", "Citas", MessageBoxButtons.OK, MessageBoxIcon.Information);
                TxtPeso.Focus();
            }
            else if (TxtTemperatura.Text == "")
            {
                MessageBox.Show("Falta la Temperatura!!", "Citas", MessageBoxButtons.OK, MessageBoxIcon.Information);
                TxtTemperatura.Focus();
            }
            else if (TxtPresion.Text == "")
            {
                MessageBox.Show("Falta la presión!!", "Citas", MessageBoxButtons.OK, MessageBoxIcon.Information);
                TxtPresion.Focus();
            }
            else
            {
                try
                {

                    if (Estado == true)
                    {
                        GuardaNuevo();
                        MessageBox.Show("Registro Guardado", "Citas", MessageBoxButtons.OK, MessageBoxIcon.Information);
                        BtnGuardar.Enabled = false;
                        BtnBuscarReg.Enabled = false;
                        BtnAgregar.Enabled = false;
                    }
                    else
                    {
                        modifica();
                        MessageBox.Show("Los cambios de Guardaron Correctamente!!", "Citas", MessageBoxButtons.OK, MessageBoxIcon.Information);
                        BtnGuardar.Enabled = false;
                        BtnBuscarReg.Enabled = false;
                        BtnAgregar.Enabled = false;
                    }
                }
                catch
                {
                    MessageBox.Show("Error!!", "Citas");
                }
            }
        }

        private void FrmCitas_Load(object sender, EventArgs e)
        {
            this.AutoClave();
           
            if (Estado == false)
            {
                CargaEditar();
            }
            CargaDoctores();
        }

        private void obtiene_datos()
        {

            MySqlConnection cnn = new MySqlConnection(Conexion.cad);
            cnn.Open();
            MySqlDataAdapter da = new MySqlDataAdapter("select Clave_Pacientes,Nombre,ApellidoPat,ApellidoMat from TblPacientes where Clave_Pacientes =" + TxtClvPaciente.Text, cnn);
            DataTable dataTable = new DataTable();
            DataSet ds = new DataSet();
            da.Fill(ds);
            if (ds.Tables[0].Rows.Count > 0)
            {
                TxtNombre.Text = ds.Tables[0].Rows[0].ItemArray[1].ToString();
                TxtApPat.Text = ds.Tables[0].Rows[0].ItemArray[2].ToString();
                TxtApMat.Text = ds.Tables[0].Rows[0].ItemArray[3].ToString();
            }
            else
            {
                MessageBox.Show("La clave del Paciente No existe!!, Debe agregarla", "Citas", MessageBoxButtons.OK, MessageBoxIcon.Information);
                BtnAgregar.Enabled = true;
            }
        }
        public void AutoClave()
        {
            MySqlConnection cnn = new MySqlConnection(Conexion.cad);
            cnn.Open();

            MySqlDataAdapter da = new MySqlDataAdapter("select FolioCitas from TblCitas ", cnn);
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
                }
                TxtFolioCitas.Text  = t.ToString();

            }
        }
        private void BtnBuscarReg_Click(object sender, EventArgs e)
        {
            
           obtiene_datos();
        }

        private void TxtClvPaciente_TextChanged(object sender, EventArgs e)
        {
            if(TxtClvPaciente.Text=="")
                BtnBuscarReg.Enabled = false;
            else
            BtnBuscarReg.Enabled = true;

        }

        private void DtpFecha_ValueChanged(object sender, EventArgs e)
        {
            TxtFecha.Text=DtpFecha.Value.ToShortDateString();
        }

        private void TxtClvPaciente_KeyPress(object sender, KeyPressEventArgs e)
        {
            if (!char.IsControl(e.KeyChar) && !char.IsDigit(e.KeyChar))
            {
                e.Handled = true;
            }
            base.OnKeyPress(e);
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

        private void MskHora_KeyPress(object sender, KeyPressEventArgs e)
        {
            if (!char.IsControl(e.KeyChar) && !char.IsDigit(e.KeyChar))
            {
                e.Handled = true;
            }
            base.OnKeyPress(e);
        }

        private void TxtEstatura_KeyPress(object sender, KeyPressEventArgs e)
        {
            if (!char.IsControl(e.KeyChar) && !char.IsDigit(e.KeyChar) && !char.IsPunctuation(e.KeyChar))
            {
                e.Handled = true;
            }
            base.OnKeyPress(e);
        }

        private void TxtPeso_KeyPress(object sender, KeyPressEventArgs e)
        {
            if (!char.IsControl(e.KeyChar) && !char.IsDigit(e.KeyChar) && !char.IsPunctuation(e.KeyChar))
            {
                e.Handled = true;
            }
            base.OnKeyPress(e);
        }

        private void TxtTemperatura_KeyPress(object sender, KeyPressEventArgs e)
        {
            if (!char.IsControl(e.KeyChar) && !char.IsDigit(e.KeyChar))
            {
                e.Handled = true;
            }
            base.OnKeyPress(e);
        }

        private void TxtPresion_KeyPress(object sender, KeyPressEventArgs e)
        {
            if (!char.IsControl(e.KeyChar) && !char.IsDigit(e.KeyChar))
            {
                e.Handled = true;
            }
            base.OnKeyPress(e);
        }

        private void TxtHora_KeyPress(object sender, KeyPressEventArgs e)
        {
            if (!char.IsControl(e.KeyChar) && !char.IsDigit(e.KeyChar) && !char.IsPunctuation(e.KeyChar))
            {
                e.Handled = true;
            }
            base.OnKeyPress(e);
        }
        
    }
}
