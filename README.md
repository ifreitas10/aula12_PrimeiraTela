//# aula12_PrimeiraTela

import javax.swing.*;
import javax.swing.plaf.metal.MetalButtonUI;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

/**
 * Created by aluno on 10/05/2018.
 */
public class AulaJavaSwing extends JFrame implements ActionListener{

    private JLabel rotuloMatriculaAluno;
    private JLabel rotuloTurmaAluno;
    private JLabel rotuloNomeAluno;
    private JLabel rotuloEnderecoAluno;
    private JLabel rotuloTelefoneAluno;
    private JLabel rotuloCpfAluno;

    private JTextField campoMatriculaAluno;
    private JTextField campoTurmaAluno;
    private JTextField campoNomeAluno;
    private JTextField campoEnderecoAluno;
    private JTextField campoTelefoneAluno;
    private JTextField campoCpfAluno;
    private JRadioButtonMenuItem campoOpcaoAluno;
    private JRadioButtonMenuItem campoOpcaoExAluno;

    private JSeparator separarCampos1;
    private JSeparator separarCampos2;

    private JButton botaoConfirmar;
    private JButton botaoAtualizar;
    private JButton botaoFechar;

    public static void main(String[] args){
        AulaJavaSwing janela = new AulaJavaSwing();
        janela.iniciarSistema();
        janela.setVisible(true);
    }

    public void iniciarSistema(){
        criarLabels();
        criarCampos();
        criarBotoes();
        criarPainel();
        montarTela();
        criarMenu();
        centralizar();
    }

    private void criarBotoes(){
        botaoConfirmar = new JButton("Consultar");
        botaoConfirmar.setBounds(35,190,100,23);
        botaoConfirmar.setMnemonic('C');
        botaoConfirmar.addActionListener(this);

        botaoAtualizar = new JButton ("Atualizar");
        botaoAtualizar.setBounds(142,190,100,23);
        botaoAtualizar.addActionListener(this);

        botaoFechar = new JButton ("Fechar");
        botaoFechar.setBounds(250,190,100,23);
        botaoFechar.addActionListener(this);
    }

    private void centralizar(){
        Dimension screen =
                Toolkit.getDefaultToolkit().getScreenSize();
        Dimension janela = getSize();

        if (janela.height > screen.height){
            setSize(janela.width, screen.height);
        }
        if (janela.width > screen.width){
            setSize(screen.width, janela.height);
        }

        setLocation((screen.width - janela.width) / 2,
                (screen.height - janela.height) / 2);

    }

    private void criarMenu(){
        //Criando os menus
        JMenu menuArquivo = new JMenu("Arquivo");
        JMenu menuSobre = new JMenu ("Sobre");
        JMenu menuEditar = new JMenu("Editar");
        JMenu subMenuSalvar = new JMenu("Salvar");

        //Criando itens do menu
        JMenuItem itemMenuAbrir = new JMenuItem("Abrir");
        JMenuItem itemMenuSair = new JMenuItem("Sair");
        JMenuItem itemMenuSalvar = new JMenuItem("Salvar");
        JMenuItem itemMenuSalvarComo = new JMenuItem("Salvar como");

        subMenuSalvar.add(itemMenuSalvar);
        subMenuSalvar.add(itemMenuSalvarComo);

        menuArquivo.add(itemMenuAbrir);
        menuArquivo.add(itemMenuSalvar);
        menuArquivo.addSeparator();
        menuArquivo.add(itemMenuSair);

        JMenuBar menuCompleto = new JMenuBar();

        menuCompleto.add(menuArquivo);
        menuCompleto.add(menuSobre);
        menuCompleto.add(menuEditar);
        setJMenuBar(menuCompleto);

    }

    private void montarTela(){
        add(rotuloMatriculaAluno);
        add(rotuloTurmaAluno);
        add(rotuloNomeAluno);
        add(rotuloEnderecoAluno);
        add(rotuloTelefoneAluno);
        add(rotuloCpfAluno);

        add(campoMatriculaAluno);
        add(campoTurmaAluno);
        add(campoNomeAluno);
        add(campoEnderecoAluno);
        add(campoTelefoneAluno);
        add(campoCpfAluno);
        add(campoOpcaoAluno);
        add(campoOpcaoExAluno);

        add(separarCampos1);
        add(separarCampos2);

        add(botaoConfirmar);
        add(botaoAtualizar);
        add(botaoFechar);
    }

    private void criarPainel(){
        setSize(400,300);
        setTitle("Linguagem de Programação V");
        setResizable(false);
        getContentPane().setLayout(null);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }

    private void criarCampos(){
        //primeira parte dos campo da tabela.
        campoMatriculaAluno = new JTextField();
        campoMatriculaAluno.setBounds(105,10,75,20);

        campoTurmaAluno = new JTextField();
        campoTurmaAluno.setBounds(285,10,80,20);

        //segunda parte dos campo da tabela.
        campoNomeAluno = new JTextField();
        campoNomeAluno.setBounds(70,50,300,20);

        campoEnderecoAluno = new JTextField();
        campoEnderecoAluno.setBounds(70,75,300,20);

        campoTelefoneAluno = new JTextField();
        campoTelefoneAluno.setBounds(70,100,300,20);

        campoCpfAluno = new JTextField();
        campoCpfAluno.setBounds(70,125,300,20);

        //terceira parte do campo tabela.
        campoOpcaoAluno = new JRadioButtonMenuItem("Aluno");
        campoOpcaoAluno.setBounds(122,145,100,23);


        campoOpcaoExAluno = new JRadioButtonMenuItem("Ex Aluno");
        campoOpcaoExAluno.setBounds(240,145,100,23);
    }

    private void criarLabels() {
        //Primeira parte das tabelas.
        rotuloMatriculaAluno = new JLabel("Matricula Aluno:");
        rotuloMatriculaAluno.setBounds(10, 10, 110, 18);

        rotuloTurmaAluno = new JLabel ("Turma do Aluno:");
        rotuloTurmaAluno.setBounds(188,10,110,18);

        //Separar as tabelas.
        separarCampos1 = new JSeparator();
        separarCampos1.setBounds(10,40,365,10);
        separarCampos2 = new JSeparator();
        separarCampos2.setBounds(10,180,365,10);

        //Segunda parte das tabelas.
        rotuloNomeAluno = new JLabel ("Nome:");
        rotuloNomeAluno.setBounds(30,50,110,18);

        rotuloEnderecoAluno = new JLabel ("Endereço:");
        rotuloEnderecoAluno.setBounds(10,75,110,18);

        rotuloTelefoneAluno = new JLabel ("Telefone:");
        rotuloTelefoneAluno.setBounds(15,100,110,18);

        rotuloCpfAluno = new JLabel ("CPF:");
        rotuloCpfAluno.setBounds(40,125,110,18);

    }

    @Override
    public void actionPerformed(ActionEvent eventoTela){
        JOptionPane.showMessageDialog(this,"Matrícula: "+campoMatriculaAluno.getText()+"\nTurma: "+campoTurmaAluno.getText()+"\nNome: "+campoNomeAluno.getText()+"\nEndereço: "+campoEnderecoAluno.getText()+"\nTelefone: "+campoTelefoneAluno.getText()+"\nCPF: "+campoCpfAluno.getText());
    }
}
