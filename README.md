# RPSLS
Rock Paper Scissors Lizard Spock: An interactive two-player game where old school meets sci-fi.


public partial class frmMain : Form
    {
        string plyr1 = "";
        string plyr2 = "";
        int round = 1;
        int score1 = 0;
        int score2 = 0;

        public frmMain()
        {

            InitializeComponent();
        }
        private void groupBox1_Enter(object sender, EventArgs e)
        {

        }

        private void btnNew_Click(object sender, EventArgs e)
        {
            txtGameLog.Text = String.Empty;
            txtPlayer1Score.Text = String.Empty;
            ResetControls(ref grpBoxPlayer1);
            ResetControls(ref grpBoxPlayer2);
        }
        private void ResetControls(ref GroupBox c)
        {
            foreach (Button r in c.Controls)
            {
                r.BackColor = DefaultBackColor;
                
            }
        }

        private void btnRound_Click(object sender, EventArgs e)
        {

            txtGameLog.Text += (txtPlayer1.Text + "" + " vs"  + "" + txtPlayer2.Text + ".  Round:" + round++ + "\r\n");
            ResetControls(ref grpBoxPlayer1);
            ResetControls(ref grpBoxPlayer2);
        }

        private void btnClose_Click(object sender, EventArgs e)
        {
            this.Close();
        }

        private void btnStart_Click(object sender, EventArgs e)
        {
            StartGame();
    
            grpBoxPlayer1.Enabled = true;
            grpBoxPlayer2.Enabled = true;
            txtGameLog.Text = (txtPlayer1.Text + "" + " vs"  + "" + txtPlayer2.Text + ".  Round:" + round++ + "\r\n");

        }

        private void txtWinner_TextChanged(object sender, EventArgs e)
        {

        }

        private void Player1Button_Click(object sender, EventArgs e)
        {

            if (sender == btnRockP1)
            {
                plyr1 = "Rock";
            }
            if (sender == btnPaperP1)
            {
                plyr1 = "Paper";
            }
            if (sender == btnScP1)
            {
                plyr1 = "Scissors";
            }
            if (sender == btnLizP1)
            {
                plyr1 = "Lizard";
            }
            if (sender == btnSpP1)
            {
                plyr1 = "Spock";
            }
            grpBoxPlayer1.Enabled = false;
            grpBoxPlayer2.Enabled = true;
        }

        private void Player2Button_Click(object sender, EventArgs e)
        {
            if (sender == btnRockP2)
            {
                plyr2 = "Rock";
            }
            if (sender == btnPaperP2)
            {
                plyr2 = "Paper";
            }
            if (sender == btnScP2)
            {
                plyr2 = "Scissors";
            }
            if (sender == btnLizP2)
            {
                plyr2 = "Lizard";
            }
            if (sender == btnSpP2)
            {
                plyr2 = "Spock";
            }
            grpBoxPlayer1.Enabled = true;
            grpBoxPlayer2.Enabled = true;

            decideWinner();
        }
        private void decideWinner()
        {
            int.TryParse(txtPlayer1Score.Text, out score1);
            int.TryParse(txtPlayer2Score.Text, out score2);

            if (plyr1 == "Rock" || plyr2 == "Rock" )
            {
                rockMove();
              
            }
            if (plyr1 == "Paper" || plyr2 == "Paper")
            {
                paperMove();
            }
            if(plyr1 == "Scissors" || plyr2 == "Scissors")
            {
                scissorsMove();
            }
            if (plyr1 == "Lizard" || plyr2 == "Lizard")
            {
                lizardMove();
            }
            if (plyr1== "Spock" || plyr2 == "Spock")
            {
                spockMove();
            }
            txtPlayer1Score.Text = score1.ToString();
            txtPlayer2Score.Text = score2.ToString();
        }
        private void rockMove()
        {
            if (plyr1 == "Rock" && plyr2 == "Rock")
            {
                btnRockP1.BackColor = Color.Yellow;
                txtGameLog.Text += "A tie! No one wins";
            }
            else if (plyr1 == "Rock" && plyr2 == "Lizard")
            {
                btnRockP1.BackColor = Color.Green;
                btnLizP2.BackColor = Color.Red;
                txtGameLog.Text += txtPlayer1.Text + "Wins!" + "\r\n" ;
                score1++;
                txtGameLog.Text += "Rock crushes Lizard" + "\r\n";
            }
            else if (plyr1 == "Rock" && plyr2 == "Scissors")
            {
                btnRockP1.BackColor = Color.Green;
                btnScP2.BackColor = Color.Red;
                txtGameLog.Text += txtPlayer1.Text + "Wins!" + "\r\n";
                score1++;
                txtGameLog.Text += "Rock crushes Scissors" + "\r\n";
            }
            if (plyr2 == "Rock" && plyr1 == "Lizard")
            {
                btnRockP2.BackColor = Color.Green;
                btnLizP1.BackColor = Color.Red;
                txtGameLog.Text += txtPlayer2.Text + "Wins!" + "\r\n";
                score2++;
                txtGameLog.Text += "Rock crushes Lizard" + "\r\n";
            }
            else if (plyr2 == "Rock" && plyr1 == "Scissors")
            {
                btnRockP2.BackColor = Color.Green;
                btnScP1.BackColor = Color.Red;
                txtGameLog.Text += txtPlayer2.Text + "Wins!" + "\r\n";
                score2++;
                txtGameLog.Text += "Rock crushes Scissors" + "\r\n";
            }
            
        }
        private void paperMove()
        {
            if (plyr1 == "Paper" && plyr2 == "Paper")
            {
                btnRockP1.BackColor = Color.Yellow;
                txtGameLog.Text += "A tie! No one wins";
            }
            else if (plyr1 == "Paper" && plyr2 == "Rock")
            {
                btnPaperP1.BackColor = Color.Green;
                btnRockP2.BackColor = Color.Red;
                txtGameLog.Text += txtPlayer1.Text  + "Wins!" + "\r\n";
                score1++;
                txtGameLog.Text += "Paper covers Rock" + "\r\n";
            }
            else if (plyr1 == "Paper" && plyr2 == "Spock")
            {
                btnPaperP1.BackColor = Color.Green;
                btnSpP2.BackColor = Color.Red;
                txtGameLog.Text += txtPlayer1.Text + "Wins!" + "\r\n";
                score1++;
                txtGameLog.Text += "Paper disproves Spock" + "\r\n";
            }
            if (plyr2 == "Paper" && plyr1 == "Rock")
            {
                btnPaperP2.BackColor = Color.Green;
                btnRockP1.BackColor = Color.Red;
                txtGameLog.Text += txtPlayer2.Text + "Wins!" + "\r\n";
                score2++;
                txtGameLog.Text += "Paper covers Rock" + "\r\t";
            }
            else if (plyr2 == "Paper" && plyr1 == "Spock")
            {
                btnPaperP2.BackColor = Color.Green;
                btnSpP1.BackColor = Color.Red;
                txtGameLog.Text += txtPlayer2.Text + "Wins!" + "\r\n";
                score2++;
                txtGameLog.Text += "Paper disproves Spock" + "\r\n";
            }
        }
        private void scissorsMove()
        {
            if (plyr1 == "Scissors" && plyr2 == "Scissors")
            {
                btnRockP1.BackColor = Color.Yellow;
                txtGameLog.Text += "A tie! No one wins";
            }
            else if (plyr1 == "Scissors" && plyr2 == "Paper")
            {
                btnScP1.BackColor = Color.Green;
                btnPaperP2.BackColor = Color.Red;
                txtGameLog.Text += txtPlayer1.Text + "Wins!" + "\r\n";
                score1++;
                txtGameLog.Text += "Scissors cuts Paper" + "\r\n";
            }
            else if (plyr1 == "Scissors" && plyr2 == "Lizard")
            {
                btnScP1.BackColor = Color.Green;
                btnLizP2.BackColor = Color.Red;
                txtGameLog.Text += txtPlayer1.Text + "Wins!" + "\r\n";
                score1++;
                txtGameLog.Text += "Scissors decapitates Lizard" + "\r\n";
            }
            if (plyr2 == "Scissors" && plyr1 == "Paper")
            {
                btnScP2.BackColor = Color.Green;
                btnPaperP1.BackColor = Color.Red;
                txtGameLog.Text += txtPlayer2.Text + "Wins!" + "\r\n";
                score2++;
                txtGameLog.Text = "Scissors cuts Paper" + "\r\n";
            }
            else if (plyr2 == "Scissors" && plyr1 == "Lizard")
            {
                btnScP2.BackColor = Color.Green;
                btnLizP1.BackColor = Color.Red;
                txtGameLog.Text += txtPlayer2.Text + "Wins!" + "\r\n";
                score2++;
                txtGameLog.Text += "Scissors decapitates Lizard" + "\r\n" ;
            }
        }
        private void lizardMove()
        {
            if (plyr1 == "Lizard" && plyr2 == "Lizard")

            {
                btnRockP1.BackColor = Color.Yellow;
                txtGameLog.Text += "A tie! No one wins";
            }
            else if (plyr1 == "Lizard" && plyr2 == "Spock")

            {
                btnLizP1.BackColor = Color.Green;
                btnSpP2.BackColor = Color.Red;
                txtGameLog.Text += txtPlayer1.Text + "Wins!" + "\r\n";
                score1++;
                txtGameLog.Text += "Lizard poisons Spock" + "\r\n";
            }
            else if (plyr1 == "Lizard" && plyr2 == "Paper")
            {
                btnLizP1.BackColor = Color.Green;
                btnPaperP2.BackColor = Color.Red;
                txtGameLog.Text += txtPlayer1.Text + "Wins!" + "\r\n";
                score1++;
                txtGameLog.Text += "Lizard eats Paper" + "\r\n";
            }
            if (plyr2 == "Lizard" && plyr1 == "Spock")
            {
                btnLizP2.BackColor = Color.Green;
                btnSpP1.BackColor = Color.Red;
                txtGameLog.Text += txtPlayer1.Text + "Wins!" + "\r\n";
                score2++;
                txtGameLog.Text += "Lizard poisons Spock" + "\r\n";
            }
            else if (plyr2 == "Lizard" && plyr1 == "Paper")
            {
                btnLizP2.BackColor = Color.Green;
                btnPaperP1.BackColor = Color.Red;

                txtGameLog.Text += txtPlayer2.Text + "Wins!" + "\r\n";
                score2++;
                txtGameLog.Text += "Lizard eats Paper" + "\r\n";
            }
        }
        private void spockMove()
        {
            if (plyr1 == "Spock" && plyr2 == "Spock")
            {
                btnRockP1.BackColor = Color.Yellow;
                txtGameLog.Text += "A tie! No one wins";
            }
            else if (plyr1 == "Spock" && plyr2 == "Rock")
            {
                btnSpP1.BackColor = Color.Green;
                btnRockP2.BackColor = Color.Red;
                txtGameLog.Text += txtPlayer1.Text + "Wins!" + "/r/n";
                score1++;
                txtGameLog.Text += "Spock vaporizes Rock" + "/r/n";
            }
            else if (plyr1 == "Spock" && plyr2 == "Scissors")
            {
                btnSpP1.BackColor = Color.Green;
                btnScP2.BackColor = Color.Red;
                txtGameLog.Text += txtPlayer1.Text + "Wins!" + "/r/n";
                score1++;
                txtGameLog.Text += "Spock smashes Scissors" + "/r/n";
            }
             if (plyr2 == "Spock" && plyr1 == "Rock")
            {
                btnSpP2.BackColor = Color.Green;
                btnRockP1.BackColor = Color.Red;
                txtGameLog.Text += txtPlayer2.Text + "Wins!" + "/r/n";
                score2++;
                txtGameLog.Text += "Spock vaporizes Rock" + "/r/n";
            }
            else if (plyr2 == "Spock" && plyr1 == "Scissors")
            {
                btnSpP2.BackColor = Color.Green;
                btnScP1.BackColor = Color.Red;
                txtGameLog.Text += txtPlayer2.Text + "Wins!" + "/r/n";
                score2++;
                txtGameLog.Text += "Spock smashes Scissors" + "/r/n";
            }
        }
        private void StartGame()
        {

            grpBoxPlayer1.Text = txtPlayer1.Text;
            grpBoxPlayer2.Text = txtPlayer2.Text;
            
            lblPlayer1Score.Text = txtPlayer1.Text;
             lblPlayer2Score.Text = txtPlayer2.Text;
        }

    }
}
