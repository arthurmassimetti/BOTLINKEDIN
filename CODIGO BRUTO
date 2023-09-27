import re
import time
import pyodbc
from selenium import webdriver
from selenium.webdriver.support.wait import WebDriverWait
from selenium.webdriver.common import by
from selenium.webdriver import Keys
from selenium.webdriver.common.by import By
from selenium.common.exceptions import NoSuchElementException
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

navegador = webdriver.Chrome()

urlgov = "https://www.linkedin.com/feed/"
navegador.get(urlgov)
navegador.maximize_window()
wait = WebDriverWait(navegador, 30)
loginja = navegador.find_element(By.XPATH, "/html/body/div[1]/main/div/p/a").click()
time.sleep(1)
emailclick = navegador.find_element(By.XPATH, "/html/body/div/main/div[2]/div[1]/form/div[1]/input").click()
time.sleep(1)
emailsend = navegador.find_element(By.XPATH, "/html/body/div/main/div[2]/div[1]/form/div[1]/input").send_keys("EMAIL AQUI") #Aqui você coloca seu email de acesso
time.sleep(1)
senhaclick = navegador.find_element(By.XPATH, "/html/body/div/main/div[2]/div[1]/form/div[2]/input").click()
time.sleep(1)
senhasend = navegador.find_element(By.XPATH, "/html/body/div/main/div[2]/div[1]/form/div[2]/input").send_keys("SENHA AQUI") #Aqui você coloca sua senha do Linkedin
time.sleep(1)
entrarclick = navegador.find_element(By.XPATH, "/html/body/div/main/div[2]/div[1]/form/div[3]/button").click()
time.sleep(2)
wait = WebDriverWait(navegador, 30)
pesquisar = navegador.find_element(By.XPATH, "/html/body/div[5]/header/div/div/div/div[1]/input").click()
pesquisarnome = navegador.find_element(By.XPATH, "/html/body/div[5]/header/div/div/div/div[1]/input").send_keys("programador")
time.sleep(1)
pesquisar2 = navegador.find_element(By.XPATH, "/html/body/div[5]/header/div/div/div/div[1]/input").send_keys(Keys.ENTER)
time.sleep(3)
wait = WebDriverWait(navegador, 30)
pessoas = navegador.find_element(By.XPATH, "/html/body/div[5]/div[3]/div[2]/section/div/nav/div/ul/li[2]/button").click()
time.sleep(2)
wait = WebDriverWait(navegador, 30)
#Bem vindo ao looping, está parte é responsavel por repetir o processo de: localizar as palavras "CONECTAR" dentro da pagina, clicar uma por uma, adicionar nota e escrever um breve texto pegando o primeiro nome do usuario, quando termina a pagina, ele segue para a outra mantendo os mesmo processos
try:
    while True:

        avancar_button = None
        try:
            wait = WebDriverWait(navegador, 30)
            avancar_button = wait.until(EC.presence_of_element_located((By.XPATH, '//button[contains(@aria-label, "Avançar")]')))
        except NoSuchElementException:
            pass

        if avancar_button:

            try:
                avancar_button.click()
            except Exception:
                pass


        botoes_conectar = None
        try:
            wait = WebDriverWait(navegador, 30)
            botoes_conectar = wait.until(EC.presence_of_all_elements_located((By.XPATH, '//span[text()="Conectar"]')))
        except NoSuchElementException:
            pass

        if not botoes_conectar:
            break

        for botao in botoes_conectar:
            botao.click()


            nome_do_usuario = navegador.find_element(By.XPATH, '//strong').text
            nome_completo = nome_do_usuario
            primeiro_nome = nome_completo.split()[0]


            navegador.find_element(By.XPATH, '//button[contains(@aria-label, "Adicionar nota")]').click()


            campo_texto = navegador.find_element(By.ID, 'custom-message')
            mensagem = f'Olá {primeiro_nome},\n\nEspero que esteja bem! Gostaria de nos conectar para trocarmos ideias e experiências sobre programação e desenvolvimento. Acredito que podemos aprender muito um com o outro e crescer juntos na nossa área.\n\nFico aguardando sua conexão!\n\nAtenciosamente,\n[Seu Nome]'
            campo_texto.clear()
            campo_texto.send_keys(mensagem)


            navegador.find_element(By.XPATH, '//button[contains(@aria-label, "Enviar")]').click()

except Exception as e:
    print(f"Ocorreu um erro: {str(e)}")
