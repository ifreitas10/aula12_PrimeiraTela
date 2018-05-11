# aula12_PrimeiraTela

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

/**
 * Created by aluno on 10/05/2018.
 */
public class AulaJavaSwing extends JFrame implements ActionListener{

private JLabel rotuloMatricula;
private JTextField campoMatricula;
private JSeparator separarCampos1;
private JButton botaoConfirmar;


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
        add(rotuloMatricula);
        add(campoMatricula);
        add(separarCampos1);
        add(botaoConfirmar);
    }

    private void criarPainel(){
        setSize(400,300);
        setTitle("Linguagem de Programação V");
        setResizable(false);
        getContentPane().setLayout(null);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }

    private void criarCampos(){
        campoMatricula = new JTextField();
        campoMatricula.setBounds(125,10,50,20);
    }

    private void criarLabels() {
        rotuloMatricula = new JLabel("Matricula Aluno");
        rotuloMatricula.setBounds(10, 10, 110, 18);

        separarCampos1 = new JSeparator();
        separarCampos1.setBounds(10,40,365,10);
    }

    @Override
    public void actionPerformed(ActionEvent eventoTela){


        JOptionPane.showMessageDialog(this,campoMatricula.getText());
    }
}
