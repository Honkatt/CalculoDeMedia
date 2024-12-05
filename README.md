```"use strict";

const p1 = document.getElementById("p1");
const p2 = document.getElementById("p2");
const saida = document.getElementById("saida");
const btnCalcular = document.getElementById("btnCalcular");
const btnSalvar = document.getElementById("btnSalvar");
const btnMostrar = document.getElementById("btnMostrar");
const btnLimpar = document.getElementById("btnLimpar");
const arrMedias = [];

//FUNÇÕES---------------------------------------------------

function obterNota(nota){
    return parseFloat(document.getElementById(nota).value);
}

function calcularMedia(p1, p2){
    return (p1+2*p2)/3;
}

function exibirSaida(mensagem){
    saida.textContent = mensagem;
}

function validarNota(nota){
    return nota >= 0 && nota < 11;
}

function calcularMediaOnClick(){
    const notaP1 = obterNota("p1");
    const notaP2 = obterNota("p2");

    if (validarNota(notaP1) && validarNota(notaP2)){
        const mediaCalculada = calcularMedia(notaP1, notaP2);
        exibirSaida(mediaCalculada.toFixed(2));
    } else {
        exibirSaida("As notas precisam ser válidas.")
    }
}

function salvarMediaOnClick() {
    const notaP1 = obterNota("p1");
    const notaP2 = obterNota("p2");

    if (validarNota(notaP1) && validarNota(notaP2)){
        const mediaCalculada = calcularMedia(notaP1, notaP2);
        arrMedias.push(mediaCalculada);
        exibirSaida(`Média ${mediaCalculada.toFixed(2)} salva com sucesso!`);
    }
}

function mostraListaOnClick() {
    if (arrMedias.length === 0){
        exibirSaida("Nenhuma média salva!");
        return;
    }
    let listaMedias = "<ol>";
    arrMedias.forEach(media => {
        listaMedias += `<li>${media.toFixed(2)}</li>`;
    });
    listaMedias += "</ol>";

    saida.innerHTML = listaMedias;
}

function limparListaOnClick() {
    arrMedias.length = 0;
    exibirSaida("Dados removidos com sucesso!");
}

//MANIPULADORES DE EVENTOS ---------------------------------

btnCalcular.addEventListener("click", calcularMediaOnClick);
btnSalvar.addEventListener("click", salvarMediaOnClick);
btnMostrar.addEventListener("click", mostraListaOnClick);
btnLimpar.addEventListener("click", limparListaOnClick);```
