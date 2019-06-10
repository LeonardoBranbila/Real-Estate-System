# Real-Estate-System
We coding this program in C in two people, so many "parts" of this code was not my of course, for example, register of  people, login, the BIG and  INCREDIBLE welcome there. And to I will not change anything here, i dont know, but is beatiful see how this code is weird today for me kk. I will refactor this code in C # and of course try to make it better !!

===============================================CODE===============================================
int encontrou = 0,c;//A variavel encontrou é usada para o conferimento do login para saber se existe, e o C é usado como parametro de comparações.
char tipo[101],tipo1[101],valorcasa[100];/* o tipo é usado para pegar informações da senha e compara para ver se a senha  existe,
o tipo1 faz a mesma coisa só que com o login,o valoe casa é usado para pegar o valor atribuido no cadastro de residencias.*/
char nome[60],endereco[60],email[50],casa[200],data[100];//todas as variaveis aqui são usadas para pegar informações dos clientes que se cadastram
int i,opcao = 0,numl,numf;/* o I é uma variavel de comparação,opcao é usada para o menu do programa aonde a pessoa digita um número e ele vai na opção escolhida, 
o numl é usado para comparação na hora que pergunta se possui um login, e o numf é usado quando a pessoa erra o login e tenta denovo, ele pega a opção escolhida.*/
char login[100],senha[100],resposta[]="grupo",respostaa[]="123456";/* login e senha são usados para a pessoa informar o login e senha no inicio do programa,a resposta e respostaa é o login e senha usados pelos adms do programa para ter acesso a tudo.*/
char cpf[50],cnpj[50],ncasa[50],telefone[50];//todas as variaveis aqui são usadas para pegar informações dos clientes que se cadastram

FILE* arquivo;//Usada para criar um arquivo.

void TirarEspaco(char texto[]) //Função usada para deixar as palavras com espaço sem dar erro no programa
{
	int i;
    for (i=0;i<strlen(texto);i++)
    {
		if (texto[i]==' ')
		{
			texto[i]='+';
		}
	}
}

void ColocarEspaco(char texto[])//Função usada para deixar as palavras com espaço sem dar erro no programa
{
	int i;
	for (i=0;i<strlen(texto);i++)
	{
		if (texto[i]=='+')
		{
			texto[i]=' ';
		}
	}
}
int arquivo_existe(char nmarq[]) { //Função para fazer uma verificação se o arquivo de texto do programa realmente existe.
	FILE* arq = fopen(nmarq, "r");
    if (arq) {
        fclose(arq);
        return 1;
    }
    return 0;
}

void menuprincipal()//Função de menu principal com todos as opções necessarias para o cliente usar.
{
	
printf("Bem vindo:%s",login);                                           printf("                                               Lumbrimoveis.ltda              (V)1.00 \n");
	
printf("=======================================================================================================================================\n");//usado só para enfeitar o programa.
printf("=======================================================================================================================================\n");
printf("(1) - Realizar cadastro oficial.");                      printf("           (2) - Ver todos os cadastros de clientes. (ADM)");
	printf("\n\n");//usado para pular linhas.
	printf("(3) - Excluir um cadastro de cliente.(ADM)");           printf(" (4) - Mostrar todas as casas disponiveis.");
	printf("\n\n");
	printf("(5) - Cadastrar novas casas.(ADM)");                     printf("          (6) - LogOff");
	printf("\n\n");
	printf("(7) - Realizar simulação de multa. ");                   printf("        (8) - Excluir Residências.(ADM)\n");
    printf("\n");
	printf("(9) - Cadastro de Imovel para locação.");               printf("     (10) - SAC.");
	printf("\n\n");
	printf("(11)- Sair do programa.\n");                         
	printf("=======================================================================================================================================\n");
	printf("=======================================================================================================================================\n");
	printf("Entre com a opção desejada: ");
	scanf("%i", &opcao);
	fflush(stdin);
	system("cls");
  
  }
void cadastro()//Aqui é onde os cliente podem realizar um cadastro oficial para ficar registrado no sistema.
{
     char comp[60];
     
   setlocale(LC_ALL,"Portuguese"); 
	
printf("Bem Vindo a  imobiliaria \n");
	printf("Por favor, para usar nossos serviços com uma melhor qualidade efetue um cadastro a seguir...\n");
	if (!arquivo_existe("registro.txt"))//Funções para ver se o arquivo realmente existe, e será usada ao longo do programa.
	return;

   printf("Informe seu nome:");           
	gets(nome);
	arquivo=fopen("registro.txt","r"); //usaremos aqui a comparação para saber se o arquivo digitado ja existe, e caso exista ele retorna ao menu principal
	encontrou = 0;
	while(!feof(arquivo))    
	{
		fscanf(arquivo, "%s %s %s %s %s %s %s %s\n",comp,cpf,cnpj,endereco,ncasa,telefone,email,data); 
		ColocarEspaco(comp);
		if (strcmp(comp, nome)==0 ) 
		{
			encontrou = 1;
			
system("cls");
   Printf("Nome já cadastrado.\n");
			system("pause");		    
	        break;
		}
	}
	
fclose(arquivo);
		    
   if (encontrou!=1)
    {
  
fFflush(stdin);//Comando para limpar o buffer.
		printf("\n");
		printf("Informe Seu CPF (sem pontos): ");
		gets(cpf);
	    fflush(stdin);
	    printf("\n");
		printf("Informe o CNPJ:(caso não possua apenas digite 0000)");
		gets(cnpj);
		fflush(stdin);
		printf("\n");
		printf("Informe seu endereço (Nome da Rua ):");   //Entrada de informações pelo usúario.
		gets(endereco);
	    fflush(stdin);
	    printf("\n");
		printf("Informe o número de sua casa:");
	    gets(ncasa);
	    fflush(stdin);
		printf("\n");
	    printf("Infome seu telefone celular ou fixo:");
	    gets(telefone);
	    fflush(stdin);
	    printf("\n");
		printf("Informe seu email:");
	    gets(email);
	    fflush(stdin);
	    printf("\n");
	    printf("Informe sua data de nascimento:");
	    gets(data);
	    TirarEspaco(nome);//Isto é usado para tirar o espaço das palavras para não dar erro no programa.
	    TirarEspaco(cpf);
	    TirarEspaco(cnpj);
	    TirarEspaco(endereco);
	    TirarEspaco(ncasa);
	    TirarEspaco(telefone);
	    TirarEspaco(email);
	    TirarEspaco(data);
		arquivo= fopen("registro.txt","a+");// Está parte é usada para gravar as informações em um arquivo de texto e será usada durante todo o programa.
		//registro.txt é o arquivo que estão salvos as informações do usuario, e será usado em outras partes do programa.
	    
fprintf(arquivo,"%s %s %s %s %s %s %s %s\n",nome,cpf,cnpj,endereco,ncasa,telefone,email,data);//Aqui é aonde são passados os paramentros para a gravação do texto no arquivo criado.
	    fclose(arquivo);
	    
printf("Cadastro realizado com sucesso!!!!");

	}

}
void vercadastro()//Está função é para os administradores do programa poderem ver todos os cadastros de clientes.
{ 
   setlocale(LC_ALL,"Portuguese");
	
if (!arquivo_existe("registro.txt"))//Funções para ver se o arquivo realmente existe, e será usada ao longo do programa.
	return;
		if (!arquivo_existe("senha.txt"))//senha.txt é o arquivo aonde estarão os logins e senhas salvos.
	    return;	
     arquivo=fopen("senha.txt","r");
	
if (strcmp(resposta, login)==0  &&  strcmp(respostaa, senha)==0  )//comparação para saber se é o administrador do programa ou outro usuario,será usado ao longo do programa. 
	{
	printf("Aqui estão todos os cadastros existentes:\n");
	
arquivo=fopen("registro.txt","r");
	while(!feof(arquivo))//Usado para ler as informações somente até chegar no final do arquivo.
	{
		fscanf(arquivo,"%s %s %s %s %s %s %s %s\n",nome,cpf,cnpj,endereco,ncasa,telefone,email,data);//é usada para ler todos as informações  que estão salvas no arquivo.
		ColocarEspaco(nome);//São usadas para colocar os espaços nas palavras digitadas, serão usados ao longo do programa.
    	ColocarEspaco(cpf);
    	ColocarEspaco(cnpj);
    	ColocarEspaco(endereco);
    	ColocarEspaco(ncasa);
    	ColocarEspaco(telefone);
    	ColocarEspaco(email);
    	ColocarEspaco(data);
		
   printf("=======================================================================================================================================\n");
       printf("=======================================================================================================================================\n");
	    printf("Nome:%s\n",nome);
		printf("CPF:%s\n",cpf);
		printf("CNPJ:%s\n",cnpj);
		printf("Endereço:%s\n",endereco);
		printf("Número da casa:%s\n",ncasa); //Saida de informações em tela para o usúario ver.
		printf("Telefone:%s\n",telefone);
		printf("Email:%s\n",email);
		printf("Data de nascimento:%s\n",data);
		printf("\n\n");
	    
	}
fclose(arquivo);
	
printf("Fim de todos os cadastros existentes.");
}
else 
{
	printf("Acesso negado!");//Bloqueia caso não sejá o administrador do programa querendo usar está função e será usada ao longo do programa.
}
fclose(arquivo);
}
void excluircasas()// Função usada para excluir uma casa, pois quando é usada 
//essa função todas as outras residências que não foram pedidas serão colocadas em um novo arquivo.
{
		char tamanhocasa[100],localizacao[100],descricao[300],banheiros[100],comodos[300],opcasa[50],codigo[30];//Variaveis usadas para exluir uma casa.
	setlocale(LC_ALL,"Portuguese");
	
char casaexcluir[80];
	 if (!arquivo_existe("senha.txt"))
	    return;	
     arquivo=fopen("senha.txt","r");
	
	
if (strcmp(resposta, login)==0  &&  strcmp(respostaa, senha)==0  )// Usado para somente o administrador ter acesso a essa área
	{
	printf("\nExclusão de casas\n\n"); 
	printf("Informe o codigo da casa que deseja remover: ");
	gets(casaexcluir);
	TirarEspaco(casaexcluir);         //O usuario ira entrar com o código da casa que deseja excluir, e automaticamente sera gerado um novo arquivo sem a casa excluida.
	arquivo = fopen("casas.txt","r"); 
	FILE* novoarquivo = fopen("novas_casas.txt","w"); 
	while(!feof(arquivo))
	{
		fscanf(arquivo,"%s %s %s %s %s %s %s %s\n",codigo,opcasa,tamanhocasa,localizacao,comodos,banheiros,descricao,valorcasa);//leitura das informações do arquivo antigo.
		if (strcmp(codigo, casaexcluir)!=0) 
		{
			fprintf(novoarquivo,"%s %s %s %s %s %s %s %s\n",codigo,opcasa,tamanhocasa,localizacao,descricao,banheiros,comodos,valorcasa);//passagem das informações para o novo arquivo.
		}
	}
    
fclose(arquivo); 
	fclose(novoarquivo); 
	
system(" del casas.txt");//Usado para deletar o registro antigo.
	system("rename novas_casas.txt casas.txt");//Renomear os arquivos de texto para o funcionamento do programa ser correto.
				
printf("Fim da exclusão!");
}
else 
{
	printf("Acesso negado!");
}
fclose(arquivo);
}

void ExcluirRegistro()// Função usada para excluir um cadastro de cliente que não irá mais usar o programa, pois quando é usada 
//essa função todos os outros arquivos que não foram pedidos serão colocados em um novo arquivo.
{
	setlocale(LC_ALL,"Portuguese");
	
char nomeexcluir[80];
	 if (!arquivo_existe("senha.txt"))
	    return;	
     arquivo=fopen("senha.txt","r");
	
if (strcmp(resposta, login)==0  &&  strcmp(respostaa, senha)==0  )
	{
	printf("\nExclusão de cadastros de clientes\n\n"); 
	printf("Informe o CPF ou CNPJ que deseja remover: ");
	gets(nomeexcluir);
	ColocarEspaco(nomeexcluir);                  // O usuario irá digitar o cpf ou cnpj que deseja excluir e será gerado um novo arquivo sem o cadastro excluido.
	arquivo = fopen("registro.txt","r"); 
	FILE* arquivoNovo = fopen("novo_registro.txt","w"); 
	while(!feof(arquivo))
	{
		fscanf(arquivo,"%s %s %s %s %s %s %s %s\n",nome,cpf,cnpj,endereco,ncasa,telefone,email,data); //leitura das informações do arquivo antigo.
		if (strcmp(cpf, nomeexcluir)!=0 && strcmp(cnpj, nomeexcluir)!=0 ) 
		{
			fprintf(arquivoNovo,"%s %s %s %s %s %s %s %s\n",nome,cpf,cnpj,endereco,ncasa,telefone,email,data); //passagem das informações para o novo arquivo.
		}
	}
    
fclose(arquivo); 
	fclose(arquivoNovo); 
	
system(" del registro.txt");//Usado para deletar o registro antigo.
system("rename novo_registro.txt registro.txt");//Renomear os arquivos de texto para o funcionamento do programa ser correto.
				
printf("Fim da exclusão!");
}
else 
{
	printf("Acesso negado!");
}
fclose(arquivo);
}

void casas()//Função para realizar a inclusão de novas casas ao sistema.
{
 setlocale(LC_ALL,"Portuguese");
  char tamanhocasa[100],localizacao[100],descricao[300],banheiros[50],comodos[50],opcasa[50],codigo[30];//variaveis usadas para pegar informações referentes a residência colocadas pelo usuario.
  
  char comp[30];
  	
if (!arquivo_existe("senha.txt"))
	    return;	
     arquivo=fopen("senha.txt","r");
     
	
if (strcmp(resposta, login)==0  &&  strcmp(respostaa, senha)==0  )
  {
    printf("Informe as informações da residência que deseja cadastrar.");
	printf("\n");
	printf("Informe o código da residência:");
	gets(codigo);
	
arquivo=fopen("casas.txt","r");
	encontrou = 0;
	while(!feof(arquivo))     //while usado para saber se o código da casa já existe no programa, e caso exista, retorna ao menu principal.
	{
	fscanf(arquivo,"%s %s %s %s %s %s %s %s\n",comp,opcasa,tamanhocasa,localizacao,comodos,banheiros,descricao,valorcasa);
		ColocarEspaco(comp);
		if (strcmp(comp, codigo)==0 )  
		{
			encontrou = 1;
			
system("cls");
		printf("Código já cadastrado.\n");
		system("pause");		    
	        break;
		}
	}
	
fclose(arquivo);
	if (encontrou!=1)
    {
	printf("\n\n");
	printf("Informe o tipo de residência, Casa ou Apartamento:");
    gets(opcasa);
    printf("\n\n");
	printf("Informe o tamanho da residência metros quadrados:");
	gets(tamanhocasa);
	printf("\n\n");
	printf("Informe a localização(bairro e cidade): ");
	gets(localizacao);
	printf("\n\n");
	printf("Descreva a residência como é e tudo mais:");               //Entrada de informações para a inclusão de residências no sistema.
	gets(descricao);
	printf("\n\n");
	printf("Informe quantos banheiros possui:");
	gets(banheiros);
	printf("\n\n");
	printf("Informe quantos comodos a residência possui:");
	gets(comodos);
	printf("\n\n");
	printf("Digite o preço total:");
	gets(valorcasa);
	printf("\n\n");
	printf("Cadastro realizado com sucesso!!!");
    TirarEspaco(opcasa);
	TirarEspaco(tamanhocasa);
	TirarEspaco(localizacao);
	TirarEspaco(descricao);//tirar o espaço das palavras
	TirarEspaco(banheiros);
	TirarEspaco(comodos);

	
arquivo=fopen("casas.txt","a+");
	
	
fprintf(arquivo,"%s %s %s %s %s %s %s %s\n",codigo,opcasa,tamanhocasa,localizacao,descricao,banheiros,comodos,valorcasa);
	fclose(arquivo);
}
}
else 
{
	printf("Acesso negado!");
}
fclose(arquivo);
}

void vercasas()//Função usada para o cliente ver todas as casas disponiveis atualmente.
{
  setlocale(LC_ALL,"Portuguese");
	char tamanhocasa[100],localizacao[100],descricao[300],banheiros[100],comodos[300],opcasa[50],codigo[30];//variaveis usadas para printar informações referentes a residência colocadas pelo usuario.
 
   
   printf("Estas são todas as residências disponíveis atualmente, com todas as informações necessarias.\n");
   printf("\n\n");
 
 arquivo=fopen("casas.txt","r");
	while(!feof(arquivo))
	{
	
fscanf(arquivo,"%s %s %s %s %s %s %s %s\n",codigo,opcasa,tamanhocasa,localizacao,comodos,banheiros,descricao,valorcasa);
	ColocarEspaco(opcasa);
	ColocarEspaco(tamanhocasa);
	ColocarEspaco(localizacao);
	ColocarEspaco(comodos);
	ColocarEspaco(banheiros);
	ColocarEspaco(descricao);
	printf("\n\n");
	printf("=======================================================================================================================\n");
    printf("=======================================================================================================================\n");
    printf("Codigo da residência:");
    printf("%s",codigo);
    printf("\n\n");
    printf("Este é o tipo da residência:");
    printf("%s",opcasa);
    printf("\n\n");
    printf("Este é o tamanho total da residência:");
	printf("%s",tamanhocasa);
	printf("\n\n");
	printf("Esta é a localização aonde a residência está:");                //Saida de informações, exibidas em tela para o usuario.
	printf("%s",localizacao);
	printf("\n\n");
	printf("Aqui está uma descrição mais detalhada da residência:");
	printf("%s",comodos);
	printf("\n\n");
	printf("O total de banheiros:");
	printf("%s",banheiros);
	printf("\n\n");
	printf("O total de comodos na residência:");
	printf("%s",descricao);
	printf("\n\n");
	printf("Este é o valor total:");
	printf("%s\n",valorcasa);
	printf("\n ");
    }
fclose(arquivo);
getch();
printf("Fim de todos as residências existentes.\n");
	
}



void decod(int a[5][2500]){ // Função usada para printar o BEM VINDO na tela inicial.
    int i,j;

   for(i = 0; i < 5;++i){
        for(j = 0; j < TAMANHO;++j){  
            if((a[i][j]) == 0)  //usado para printar dois bloquinhos um ao lado do outro na tela da forma correta.
                printf("  ");       //Aonde são definidos os parametros para o enquadramento de tela.
            else
                printf("%c%c", 219,219);
        }
        printf("\n");
    }
    printf("\n");
}




void stom(int d[5][2500], char s[]){ //é a declaração de letras em codigos usaado para o BEM VINDO no inicio do programa
    short int alfabeto[28][5][5] = {{0,1,1,1,0,1,0,0,0,1,1,1,1,1,1,1,0,0,0,1,1,0,0,0,1},
    {1,1,1,1,0,1,0,0,0,1,1,1,1,1,0,1,0,0,0,1,1,1,1,1,0},
    {0,1,1,1,1,1,0,0,0,0,1,0,0,0,0,1,0,0,0,0,0,1,1,1,1},
    {1,1,1,1,0,1,0,0,0,1,1,0,0,0,1,1,0,0,0,1,1,1,1,1,0},
    {1,1,1,1,1,1,0,0,0,0,1,1,1,0,0,1,0,0,0,0,1,1,1,1,1},
    {1,1,1,1,1,1,0,0,0,0,1,1,1,0,0,1,0,0,0,0,1,0,0,0,0},
    {0,1,1,1,1,1,0,0,0,0,1,0,1,1,1,1,0,0,0,1,0,1,1,1,0},
    {1,0,0,0,1,1,0,0,0,1,1,1,1,1,1,1,0,0,0,1,1,0,0,0,1},
    {0,0,1,0,0,0,0,1,0,0,0,0,1,0,0,0,0,1,0,0,0,0,1,0,0},
    {0,0,0,0,1,0,0,0,0,1,0,0,0,0,1,1,0,0,0,1,0,1,1,1,0},
    {1,0,0,0,1,1,0,0,1,0,1,1,1,0,0,1,0,0,1,0,1,0,0,0,1},
    {1,0,0,0,0,1,0,0,0,0,1,0,0,0,0,1,0,0,0,0,1,1,1,1,1},
    {1,0,0,0,1,1,1,0,1,1,1,0,1,0,1,1,0,0,0,1,1,0,0,0,1},
    {1,0,0,0,1,1,1,0,0,1,1,0,1,0,1,1,0,0,1,1,1,0,0,0,1},
    {0,1,1,1,0,1,0,0,0,1,1,0,0,0,1,1,0,0,0,1,0,1,1,1,0},
    {1,1,1,1,0,1,0,0,0,1,1,1,1,1,0,1,0,0,0,0,1,0,0,0,0},
    {0,1,1,1,0,1,0,0,0,1,1,0,1,0,1,1,0,0,1,0,0,1,1,0,1},
    {1,1,1,1,0,1,0,0,0,1,1,1,1,1,0,1,0,0,0,1,1,0,0,0,1},
    {0,1,1,1,1,1,0,0,0,0,0,1,1,1,0,0,0,0,0,1,1,1,1,1,0},
    {1,1,1,1,1,0,0,1,0,0,0,0,1,0,0,0,0,1,0,0,0,0,1,0,0},
    {1,0,0,0,1,1,0,0,0,1,1,0,0,0,1,1,0,0,0,1,0,1,1,1,0},
    {1,0,0,0,1,1,0,0,0,1,1,0,0,0,1,0,1,0,1,0,0,0,1,0,0},
    {1,0,0,0,1,1,0,0,0,1,1,0,1,0,1,1,1,0,1,1,1,0,0,0,1},
    {1,0,0,0,1,0,1,0,1,0,0,0,1,0,0,0,1,0,1,0,1,0,0,0,1},
    {1,0,0,0,1,0,1,0,1,0,0,0,1,0,0,0,0,1,0,0,0,0,1,0,0},
    {1,1,1,1,1,0,0,0,1,0,0,0,1,0,0,0,1,0,0,0,1,1,1,1,1},
    {0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0},
	{0,0,1,0,0,0,0,1,0,0,0,0,1,0,0,0,0,0,0,0,0,0,1,0,0}};

   //int B[5][5] = {,,,,,,,,,,,,,,,,,,,,,,,,}; somente anotações.

   int i, linha=0, coluna = 0, c = 0, posicao;//variaveis usadas para o funcionamento da função.

   for(i = 0;s[i] !='\0';++i){

   if(s[i]>='A' && s[i]<='Z')  // Define qual o valor da variavel posição (que será¡ usada para indicar qual linha da matriz alfabeto corresponde ao
            posicao = s[i] - 'A';   // a letra de s[i]). Se o valor estiver entre A e Z a posição é definida de 0 a 25. Exemplo: Se s[i] = G entÃ£o a posição
        else                        // será¡ 'G'-'A' que na tabela ASCII é o mesmo que 71-65 = 6, ou seja, a letra G está¡ na 6ª linha da matriz alfabeto. Caso
		if ( s[i]=='!')             // contrario a posição corresponderá¡ ao espaço em branco.
            posicao = 27;           
         else
         posicao = 26;

   while(linha != 5 && c != 5){                             // Tranfere os valores da martiz alfabeto para a matriz d (display) da seguinte maneira:
            d[linha][coluna++] = alfabeto[(posicao)][linha][c++];// São trasferidos os valores da primeira linha, no fim da linha (quando c é igual a 5)
                if(c == 5){                                      // pulamos para a linha de baixo (linha ++), resetamos o valor de c e subitraimos 5 da coluna,
                    c = 0;                                       // o processo é repetido até o fim da trasferencia da letra.
                    linha++;                                     // (OBS:o valor da coluna não pode ser resetado porque caso contrario a proxima letra seria
                    coluna -= 5;                                 // colocada em cima das informações da letra anterior)
                }                                                //
            }                                                    //

   coluna += 5;// Reseta os valores para que a proxima letra seja colocada na posição correta.
     linha = 0;  //
        c = 0;      //

   while(linha != 5)           // Adiciona uma linha em branco entre cada letra para que elas não fiquem juntas.
            d[linha++][coluna] = 0; //
        coluna++;                   //
        linha = 0;                  //
    }
}	
void cadastroaluguel()
{

int casa[5];           // casa = vetor com as seguintes variaveis em cada locação: [1] aluguel da casa, [2] condominio, [3] multa moratoria.
	                       //[4] multa recisoria após o calculo da porcentagem.
	float morato;

//declarando funções gerais para o uso em todos os casos do programa.

int c, ncasa, codigo[200]; //c = contador, ncasa = numero da casa.
char cadastro;
char endereco[50], bairro[50]; // Nome do arquivo txt criado, endereço - nome da rua da casa.
int aluguel, aluguel2; // Variaveis de switchs.
int opcao1,opcao2;     // Variaveis de switchs 2.
int confirma; //switch
char cod[100],compp[100];//usado no codigo da residencia.

FILE* contrato1;

setlocale(LC_ALL, "Portuguese");
system("cls");
printf (" 1- CADASTRO DE UM NOVO IMOVEL PARA LOCAÇÃO: \n 2- ACESSO  UM IMOVEL JÁ CADASTRADO: \n 0- RETORNAR AO MENU INCIAL.\n\n                                    Digite a opção que deseja: \n\n "); scanf ("%i", &aluguel);
 
    
  printf ("\n\n");
switch (aluguel)
   {
   
  
   case 1: // Esse código é destinado ao locatário que deseja cadastrar seu imovel, informando no contrato, valor do aluguel, condominio, taxas da multas, etc.
  
                                                                
 
   printf("Insira o código do cadastro:"); scanf("%s",&cod);
    fflush(stdin);
    printf("\n");
    	contrato1=fopen("cadastro.txt","r"); //usaremos aqui a comparação para saber se o arquivo digitado ja existe, e caso exista ele retorna ao menu principal
	encontrou = 0;
	while(!feof(contrato1))    
	{
    	fscanf (contrato1, "  %i %i %i %i %s %s %i %s %f\n",&casa[1], &casa[2], &casa[3], &casa[4],compp,endereco, &ncasa,bairro, &morato);
		if (strcmp(compp, cod)==0 ) 
		{
			encontrou = 1;
			
system("cls");
			printf("Código já cadastrado.\n");
			system("pause");		    
	        break;
		}
	}
	fclose(contrato1);
	if (encontrou!=1)
    {
   printf ("Insira o tempo de contrato em meses: ");     scanf ("%i",&casa[1]); printf ("\n");
   printf ("Insira o aluguel desejado do seu imóvel: "); scanf ("%i",&casa[2]); printf ("\n");
   printf ("Caso seu imovel contenha um CONDOMINIO insira aqui o valor, caso não, digite zero: "); scanf ("%i",&casa [3]); printf ("\n");
   fflush(stdin);
   printf("Digite o nome da rua onde fica o imóvel: "); gets(endereco); printf ("\n"); 
   fflush(stdin);
   printf("Digite o número da casa: "); scanf("%i",&ncasa); printf ("\n");
   fflush(stdin);
   printf ("Insira o nome do Bairro: "); gets(bairro); printf ("\n"); 
   fflush(stdin);
   TirarEspaco(endereco);
   TirarEspaco(bairro);
   
   printf ("Agora insira os valores das multas em sequência: \n");
   
   
   printf ("1- RECISORIA: ");      scanf ("%i",&casa[4]); //Valor escolhido unicamente pelo dono do imovel podendo ser desde um valor fixo de 3.000 reais como ate
                                                           //uma porcentagem do aluguel. O código em si usa o exemplo de valor fixo.
   printf ("2- MORATORIA:  ");     scanf ("%f",&morato); //Lembrando ser um valor cobrado diariamente tendo então que ser ate no maximo 2% permitido por lei.
     contrato1 =  fopen ("cadastro.txt", "a+");
    for(c=1; c < 5; c++) //loop para armazenamento em arquivo.
   {
   	  fprintf (contrato1,"%i ", casa[c]);  
   }
    
   fprintf(contrato1, "%s %s %i %s %f\n",cod,endereco,ncasa,bairro, morato);
     
fclose(contrato1);
     
   break;                          printf ("\n\n");
   }
  
  
   case 2: //case 2 alteração do cadastro;
             //Essa parte daremos a pessoa cadastrada a opção de acessar seu imovel para alterações dos valores.
  
{
system ("cls");
	printf (" 1- VISUALIZAÇÃO DE CADASTRO.\n 2- EXCLUSÃO DE CADASTRO.\n 0-RETORNAR AO MENU INICIAL.\n\n                                       Digite a opção que deseja: \n\n"); 
	scanf ("%i",&opcao1);
    system ("cls");
	
if (opcao1 == 1||2)
	{
	
switch (opcao1)
   {        
			
case 1: // exibira o arquivo na tela para o usuario conferir os dados.
    
contrato1 = fopen ("cadastro.txt","r"); 
       		
while(!feof(contrato1))
	{
	    printf("=======================================================================================================================================\n");
	    printf("=======================================================================================================================================\n");
	    printf("\n\n");
	    fscanf (contrato1, "  %i %i %i %i %s %s %i %s %f\n",&casa[1], &casa[2], &casa[3], &casa[4],cod,endereco, &ncasa,bairro, &morato);
	    ColocarEspaco(endereco);
	    ColocarEspaco(bairro);
		printf (" Tempo de contrato: %i\n Aluguel: %i\n Condominio: %i\n Código: %s\n Rua: %s\n Número da casa: %i\n Bairro: %s\n Multa Recisoria: %i\n Multa moratória: %.2f \n",casa[1],casa[2],casa[3],cod,endereco,ncasa,bairro,casa[4], morato);
	}
	fclose(contrato1); // fim da leitura
	break;

  case 2: // Caso para alteração do cadastro.
  {
      char excluirr[100];
				printf ("                                      Opção Exclusão de cadastro escolhida\n\n");
  	 
printf("Informe o código da casa que deseja remover: ");
	scanf("%s",&excluirr);
	         //O usuario ira entrar com o código da casa que deseja excluir, e automaticamente sera gerado um novo arquivo sem a casa excluida.
	contrato1= fopen("cadastro.txt","r"); 
	FILE* novoarquivoo = fopen("novos_cadastros.txt","w"); 
	while(!feof(contrato1))
	{
		fscanf(contrato1, "  %i %i %i %i %s %s %i %s %f\n",&casa[1], &casa[2], &casa[3], &casa[4],cod,endereco, &ncasa,bairro, &morato);//leitura das informações do arquivo antigo.
		if (strcmp(cod, excluirr)==0)
		{
			fprintf(novoarquivoo, "%i %i %i %i %s %s %i %s %f\n",casa[1],casa[2],casa[3],casa[4],cod,endereco,ncasa,bairro, morato);//passagem das informações para o novo arquivo.
		}
	}
    
fclose(contrato1); 
	fclose(novoarquivoo); 
	
system(" del cadastro.txt");//Usado para deletar o registro antigo.
system("rename novos_cadastros.txt cadastro.txt");//Renomear os arquivos de texto para o funcionamento do programa ser correto.
				
printf("Fim da exclusão!");
  
    
  
}
   }
   }
else
  printf("     Valor invalido, provavelmento digitou algum numero que não seja um dos 5 citados. por favor tente novamente.\n"); // Mensagem de error
}
}
}
void juros()// Função usada para o calculo de juros.
{
	setlocale(LC_ALL,"Portuguese");
	printf ("                                             Qual multa deseja simular? \n\n 1- MORATORIA:\n 2- RESISORIA:\n");
      
           
  int opcao3;
          int ultimafa;
		  float  valor_total, valor_mora, moratoria,aluguel, c;
           scanf("%i", &opcao3);

           
   switch (opcao3) 
        {
          case 1:
               
  printf ("Insira a quantidade de dias passados da ultima fatura: \n");  scanf ("%i",&ultimafa); 
               printf ("digite o valor do aluguel: \n");  scanf("%f", &aluguel);
               printf ("Insira o valor da multa moratoria em percentual diario: \n" ); scanf ("%f", &valor_mora);
               
  moratoria = 0;
				for (c = 0; c < ultimafa; c++);
			{
				moratoria = ((aluguel * valor_mora)/100) + moratoria; //ou o loop roda somando as multas para mais tarde somar ao aluguel ou sempre calculo a cada
				                                                     //dia o mesmo valor de mora sobre um novo valor de aluguel uq ja esta somado com o do dia
				                                                      //anterior.
            }
                valor_total = aluguel + moratoria;
                  
		                                                        printf ("\n\n");
   
                   
  printf ("Lembrando que o locatario devera pagar %.2f por cento de multa por dia, ele pagara assim ate o dia atual inserido um total de %.2f reais.\n",valor_mora,valor_total);
               printf ("\n");
                break;

 
  int meses_alugados, mrestantes, tc,vrescisao; // meses_alugados = o tempo que a pessoa ficou no imóvel, mrestantes = o tempo que falta ate o fim do contrato, tc = tempo de contrato.  
             int valor_multa, aluguel, multa; // valor_multa = é o valor do aluguel dividido pelo Tempo de Contrato total, aluguel = aluguel da casa.
                                                            // vrescisão = é o valor total apenas da multa para o locatário, multa = valor pré-definido de multa pelo contrato.
             case 2:
              
valor_multa = 0;
			  mrestantes = 0;
			  vrescisao = 0;
			  
printf("Insira o valor da multa rescisória confirmada no contrato: \n");  scanf ("%i",&multa); 
			  printf("Insira a quantidade de meses registrado no contrato: \n");  scanf ("%i",&tc); 
			  printf("Insira a quantidade de meses que o locatário ficou no imovel:   \n");  scanf ("%i",&meses_alugados); 
			         
   valor_multa = multa / tc; // Para descobrir o valor da multa p/mes, fizemos o valor dela dividido pelos meses totais de contrato.
                mrestantes = tc - meses_alugados; // Para descobrir quantos meses faltavam para o fim do contrato, feito mes de contrato menos mes que saiu.
                vrescisao = valor_multa * mrestantes;    // valor da multa vezes o total de meses faltando para o fim do contrato, assim descobrindo o total a pagar.
                      
 printf ("Valor total da multa de rescição é de %i", vrescisao);
                
                printf ("\n\n"); 
break; 
             
default:
              system ("cls");
                printf("               Valor invalido, você digitou algum numero que não seja 1 ou o 2. Por favor tente novamente.\n");
             break;
        }
        }
        
void paralogin()//Função usada para o logoff entre outras coisas.
{

system("DVD:Imobiliaria.exe");//este é usado exclusivamente para o DVD de gravação do programa.
	system("C:Imobiliaria.exe");
	system("D:Imobiliaria.exe");    //Aqui são todos os comandos de sistemas para a entrada no hd para reabrir o programa quando for solicitado.
	system("B:Imobiliaria.exe");    //possui varios pois existem hds com nomes diferentes, assim caso ele não encontre de primeira ele pode continuar procurando nos outros.
	system("A:Imobiliaria.exe");    
    system("G:Imobiliaria.exe");
	system("F:Imobiliaria.exe");
    system("E:Imobiliaria.exe");
    
	
	
system("cls");
exit(0); //usado para fechar o programa anterior para não dar erro.

}
void sac()
{
	 setlocale(LC_ALL,"Portuguese");
     int c,parcelas;
     float MIP,MIP2,DFI, DFI2, valor_juros, juros, valor_mes,amortizacao,valor_imovel, taxa_adm;
     
/*Calculo do pagamento no sistema SAC somando 
	  com a taxa de administração e o DFI, 
	  subtraindo a amortização do total do imovel 
	  a cada parcela e multiplicando dos novos valores totais 
	  o juros e o MIP
	  deixando mes a mes a parcela mais barata*/
      
      
 //Aqui o usuario dara ao programa os dados do imóvel.

printf ("                                               SIMULADOR DO SISTEMA SAC PARA FINANCIAMENTO:\n\nInsira o valor total do imovel: "); scanf("%f",&valor_imovel);
    printf ("Quantas vezes deseja pagar o imovel: "); scanf("%i",&parcelas);
      
printf ("Insira o valor do juros: "); scanf("%f",&juros);
	  
printf ("Insira o valor do MIP (seguro por morte ou invalides): "); scanf("%f",&MIP); //Seguro normalmente dado em favor ao banco.
    
printf ("Insira o valor do DFI (seguro de danos fisicos ao imovel): "); scanf("%f",&DFI); // Seguro para a pessoa que comprou a casa, caso aconteça algo a casa
                                                                                               //no tempo em que esta sendo paga.

printf ("Insira o valor da taxa de administração da corretora: "); scanf("%f",&taxa_adm);
      
 printf ("\n\n");
      
amortizacao = valor_imovel/parcelas; // Amortização é o valor subtraido mes a mes do saldo devedor ate que a divida zere.
      DFI2 = (DFI/100)* valor_imovel; //Para encontrar o valor do DFI pago mensalmente;
      
printf ("O valor da sua amortização é %.2f:\n", amortizacao); 
      
   printf ("\n");
printf ("  valor imovel no mês\t |juros do mês\t        |MIP\t         |DFI\t            |parcela do mês\n------------------------------------------------------------------------------------------\n");
    for (c = parcelas-1 ; c > 0; c--)

 {
	 
valor_imovel = valor_imovel - amortizacao; // A subtração do saldo devedor.
    
valor_juros = (juros/100) *valor_imovel; // Valor do juros é multiplicado mes a mes pelos valores reajustados diminuindo juntamente a eles.
	
 valor_mes = ((amortizacao + valor_juros)+ taxa_adm); // O sistema SAC tem como caracteristica a diminuição das parcelas conforme o tempo.
       
 MIP2 = valor_imovel*MIP; // Seguro de morte ou invalides é multiplicado igualmente para todas as parcelas.
       
if (valor_imovel>=10000)
              printf ("  %i.\t%.2f\t |%.2f\t        |%.2f\t |%.2f\t    |%.2f\n",c, valor_imovel, valor_juros, MIP2, DFI2, valor_mes);
       else
              printf ("  %i.\t%.2f\t\t |%.2f\t        |%.2f\t |%.2f\t    |%.2f\n",c, valor_imovel, valor_juros, MIP2, DFI2, valor_mes);
       
 printf ("\n\n");
      //Caso deseje tirar duvidas sobre a forma do cálculo e/ou seguros por favor acesse: calculadorafacil.com.br/financeiro/simulador-de-financiamento-de-imoveis.
}
}



int main()//inicio do programa.
{

 
int c, i;// Variaveis usadas para o BEM VINDO na tela inicial.
    char st[500]="BEM VINDO! ";//A declaração da palavra para o uso.
    int display[5][2500];//O espaço que as letras irão usar 

    
stom(display, st); //Pega o que está escrito em st, no caso o bem vindo,e coloca os 0 e 1 dentro da matriz display.

system("cls"); 
    
  decod(display); //o decod pega os 0 e 1 e decodifica nos bloquinhos ou em espaços em branco.


setlocale(LC_ALL,"Portuguese");//Para definir a linguagem do programa em português.



printf("Por favor digite (1) caso já possua um login ou (2) caso não possua:");//Inicio do programa aonde é perguntado se o usario ja tem um login ou não.
    scanf("%i",&numl);
    system("cls");
if (numl>0 && numl<=2)
{
if (numl==1)//Comparações usadas para entrar em áreas especificas do programa.
{
		arquivo = fopen("senha.txt", "r");

getchar();	
    printf("\n\n\n\n\n\n\n\n\n");
		printf("                                                    Login:");
        gets(tipo1);                                                                           //aqui é onde o usuario informa o login e senha cadastrados.

printf("                                                    Senha:");    
    gets(tipo);    
    TirarEspaco(login);
    TirarEspaco(senha);
    system("cls");
	while(!feof(arquivo))    
	{
		fscanf(arquivo, "%s %s \n",login,senha);
		if (strcmp(tipo1,login)==0 && strcmp(tipo,senha)==0)
		{
			encontrou = 1;//Se o login e senha forem encontrados ele libera acesso ao programa.
			break;
		}
	}
	if (encontrou==0)//Caso não tenha sido encontrado um login e senha ele vai para esta opção
	{
		printf("\n\nNenhum cadastro encontrado pelo criterio de busca.\n\n");
	    printf("Digite <1> para tentar novamente ou <2> para se cadastrar");
	    scanf("%i",&numf);
	   system("cls");
	    if (numf>=1 && numf<=2)
	{
	
		
if (numf==1)
	    {
		numl=3;//chamada da função para tentar fazer o login novamente.
	    } 
       
if (numf==2)
    {
	numl=2;//vai para a parte de cadastro do login automaticamente.
	}
    }
    else
    {
    	paralogin();
	}
	}
	
   else
	{
		printf("Acesso liberado.\n");
		
	}
fclose(arquivo);
	

}
if (numl==3)//está é a segunda tentativa de login
{
		arquivo = fopen("senha.txt", "r");

getchar();	
    printf("\n\n\n\n\n\n\n\n\n");
		printf("                                                    Login:");
        gets(tipo1);

printf("                                                    Senha:");
    gets(tipo);
    TirarEspaco(login);
    TirarEspaco(senha);
    system("cls");
	while(!feof(arquivo))
	{
		fscanf(arquivo, "%s %s \n",login,senha);
		if (strcmp(tipo1,login)==0 && strcmp(tipo,senha)==0)
		{
			encontrou = 1;//Se o login e senha forem encontrados ele libera acesso ao programa.
			break;
		}
	}
	if (encontrou==0)//Caso não tenha sido encontrado um login e senha ele vai para esta opção
	{
		printf("\n\nNenhum cadastro encontrado pelo criterio de busca.\n\n");
	    printf("Digite <1> para tentar novamente ou <2> para se cadastrar");
	    scanf("%i",&numf);
	   system("cls");
	    if (numf==1)
	    {
		paralogin();//chamada da função para tentar fazer o login novamente.
	    } 
       
 if (numf==2)
    {
    	numl=2;//vai para a parte de cadastro do login automaticamente.
	}
	}
	else
	{
		printf("Acesso liberado.\n");
		
	}
fclose(arquivo);
}


if (numl==2)
{
	char comp[60];
printf("Digite o login que será usado para acessar o programa:");
scanf("%s",&login[i]);
ColocarEspaco(login);
	arquivo=fopen("senha.txt","r");
	encontrou = 0;
	while(!feof(arquivo))    
	{
	fscanf(arquivo, "%s %s \n",comp,senha);
		ColocarEspaco(comp);
		if (strcmp(comp, login)==0 )
		{
			encontrou = 1;
			system("cls");
			printf("Login já cadastrado.\n"); //Toda essa parte é usada para saber se a informação digitada pelo usuario já existe no sistema, e caso exista ele retorna ao menu de login.
			system("pause");	
			paralogin();	    
	        break;
		}
	}
	fclose(arquivo);
   if (encontrou!=1)
    {
  
 
printf("\n\n");
printf("Digite a senha que será usada:");
scanf("%s",&senha[i]);
ColocarEspaco(senha);
system("cls");
	arquivo=fopen("senha.txt","a+");
	fprintf(arquivo,"%s %s\n",login,senha);                       //está é a area aonde são cadastrados os logins, e logo depois ja tem acesso ao programa.
	fclose(arquivo);
	printf("Acesso liberado.\n");
}
	
}
}
else
{
	
paralogin();
}

setlocale(LC_ALL,"Portuguese");

while(opcao!=11)//Usado para listas as opções declaradas pelo programador.
	{
		menuprincipal();
		
switch(opcao)
		{
			case 1:
			cadastro();
			break;
			
case 2:                       //Chamadas de todas as funções do programas, quando forem solicitadas
			vercadastro();
			break;
			
case 3:
			ExcluirRegistro();
			break;
			
case 4:
				vercasas();
				break;
				
case 5:
				casas();
				break;
			
			
case 6:
				paralogin();
				break;
			
case 7:
			     juros();
				break;
		    
case 8:
		   	    excluircasas();
			   break;
			
case 9:
				cadastroaluguel();
				break;
				
case 10:
		    	sac();
			    break;		
			    
case 11:
			    	sair();
			    break;
			    
			   
			
default:
		    	printf("Opção invalida.");
		    	break;
		}
	printf("Aperte qualquer tecla para sair.");
	getch();
    system("cls");
	

	}

}

void sair()//Usado para sair do programa sem dar erros.
{
	
	
system("pause, C:Imobiliaria.exe");//ele vai até o diretorio aonde será rodado o programa  e o encerrara.
	system("pause, D:Imobiliaria.exe");
	
}
