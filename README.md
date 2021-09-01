# Botão-Login-SistemaCRUD
private void logar()
        {
            bool flag = false;
            if ((txtBoxUsuario.Text != string.Empty) && (txtBoxSenha.Text != string.Empty) && (txtBoxChave.Text != string.Empty))
            {
                string CONFIG = "server=;database=;uid=;password=";
                MySqlConnection conexao = new MySqlConnection(CONFIG);
                MySqlCommand query = new MySqlCommand();
                query.Connection = conexao;
                conexao.Open();
                query.CommandText = "SELECT nome,senha FROM `omega`.`usufunc` WHERE `nome` = '" + txtBoxUsuario.Text.Trim() + "' and `senha` = '" + txtBoxSenha.Text.Trim() + "'";
                query.CommandText = "SELECT departamento FROM `omega`.`usufunc` WHERE `departamento` = '" + txtBoxChave.Text.Trim() + "'";
                bool linhas = query.ExecuteReader().HasRows;
                if (linhas)
                { 
                    this.Hide();
                    frmPrincipal f = new frmPrincipal();
                    f.ShowDialog();
                    this.Close();
                    this.Dispose();
                }
                else
                {
                    MessageBox.Show("Usuário,senha ou departamento inválidos");
                }
                conexao.Close();
            }
            else
            {
                if (txtBoxUsuario.Text == string.Empty)
                {
                    MessageBox.Show("Preencha o campo 'Usuário'");
                    flag = true;
                }
                if (txtBoxSenha.Text == string.Empty)
                {
                    MessageBox.Show("Preencha o campo 'Senha'");
                    flag = true;
                }
                if (txtBoxChave.Text == string.Empty)
                {
                    MessageBox.Show("Preencha o campo 'Chave'");
                    flag = true;
                }
            }
        }
