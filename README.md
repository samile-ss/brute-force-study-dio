# Documentação do desafio: Ataque de força bruta com Kali Linux e Medusa
# Links no final do documento

# Justificativa sobre a Execução Prática

Durante o desenvolvimento do desafio, segui todas as aulas e tentei reproduzir os cenários utilizando duas máquinas virtuais (Kali Linux e Metasploitable 2). No entanto, ao tentar configurar a VM nos computadores da instituição, o ambiente apresentou falhas e não chegou a inicializar corretamente.

Como as máquinas são compartilhadas com outros alunos, preferi não forçar a execução para evitar travamentos ou possíveis danos ao sistema, especialmente porque o curso exigia rodar serviços vulneráveis e ferramentas que demandam mais desempenho.

Por esse motivo, não consegui realizar a prática diretamente nas VMs, mas fiz anotações completas de todo o conteúdo apresentado nas aulas, revisei os comandos e procurei entender cada etapa do processo de auditoria de segurança. Este documento reúne esse estudo — tanto a teoria quanto o passo a passo das práticas demonstradas em vídeo.


 # 1. Conceitos Fundamentais Sobre Ataques de Força Bruta

-Força Bruta é uma técnica que tenta descobrir senhas por meio de tentativas sucessivas.
-É usada tanto por atacantes quanto por analistas de segurança para fins de auditoria.
-Um ataque de força bruta pode ocorrer em:
			-Serviços FTP
			-Logins web (ex.: DVWA)
			-Serviços SMB
			-SSH, Telnet, RDP

-A eficácia depende da combinação:
		-Wordlist adequada
		-Serviço vulnerável
		-Limitação de tentativas


# 2. Ferramenta Estudada: Medusa
-O Medusa é um brute forcer rápido e modular, capaz de realizar ataques paralelos.
Comandos estudados:
   # Autenticação em FTP:
			medusa -h <IP-alvo> -u <usuario> -P <wordlist> -M ftp

   # Autenticação em serviços SMB
			medusa -h <IP> -U users.txt -P pass.txt -M smbnt

  # Autenticação em formulários web (DVWA)
			medusa -h <IP> -u admin -P senhas.txt -M web-form -m FORM:"login.php" -m DENY:"Login failed"


# 3. Cenários apresentados nas aulas
  # 3.1 FTP – Ataque de força bruta:
		Entendimento de como o protocolo funciona.
		Configuração em ambiente vulnerável (Metasploitable 2).
		Teste com wordlists curtas para validação.

   # 3.2 DVWA – Ataque em formulário web:
		Identificação de parâmetros do formulário.
		Uso de mensagens de erro para validar ou negar credenciais.
		Importância da sanitização e limitação de tentativas.

   # 3.3 SMB – Password spraying:
		Diferença entre força bruta e spraying.
		Enumeração de usuários antes do ataque.
		Impacto em ambientes corporativos.


   # 4. Boas Práticas e Medidas de Mitigação
		Ativar limite de tentativas de login.
		Implementar bloqueio temporário após falhas repetidas.
		Usar MFA (autenticação em múltiplos fatores).
		Exigir política forte de senhas.
		Monitorar logs e configurar alertas de tentativas anômalas.

   # 5. Considerações Finais
   Mesmo sem conseguir executar o laboratório em VMs devido às limitações técnicas do ambiente, o estudo possibilitou compreender o funcionamento    dos ataques, a lógica interna das ferramentas e o impacto de cada técnica na segurança dos sistemas.

   As anotações servem como base para implementação prática futura, em um ambiente mais estável e controlado.

## Evidências Complementares
Devido ao tamanho dos arquivos, os registros em imagem foram disponibilizados externamente:

👉 Acesse aqui: 
    https://drive.google.com/file/d/1trgMlme26nTCBtmHQ9ia9mHa_pe-1n26/view?usp=sharing
	https://drive.google.com/file/d/1JBXAqcXEuCvmpCz6n42VadUY_cIZDEM_/view?usp=sharing

   https://drive.google.com/file/d/1trgMlme26nTCBtmHQ9ia9mHa_pe-1n26/view?usp=sharing
