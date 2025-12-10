import os

# =========================
# CRIAR PASTA DE IMAGENS
# =========================
os.makedirs("images", exist_ok=True)

# =========================
# 1. SEXO x ESCOLARIDADE
# =========================
plt.figure()
tabela_contingencia.plot(kind="bar", stacked=True)
plt.title("Relação entre Sexo e Escolaridade")
plt.xlabel("Sexo")
plt.ylabel("Frequência")
plt.tight_layout()
plt.savefig("images/sexo_escolaridade.png", dpi=150)
plt.close()

# =========================
# 2. DISTRIBUIÇÃO DO IMC
# =========================
plt.figure()
plt.hist(imc, bins=30)
plt.axvline(media, linestyle="--", label=f"Média = {media:.2f}")
plt.axvline(mediana, linestyle="-.", label=f"Mediana = {mediana:.2f}")
plt.axvline(moda, linestyle=":", label=f"Moda = {moda:.2f}")
plt.title("Distribuição do IMC")
plt.xlabel("IMC")
plt.ylabel("Frequência")
plt.legend()
plt.tight_layout()
plt.savefig("images/imc_distribuicao.png", dpi=150)
plt.close()

# =========================
# 3. NORMALIZAÇÃO IMC
# =========================
plt.figure(figsize=(12,4))

plt.subplot(1,3,1)
plt.hist(imc, bins=30)
plt.title("IMC Original")

plt.subplot(1,3,2)
plt.hist(imc_minmax, bins=30)
plt.title("IMC - MinMax")

plt.subplot(1,3,3)
plt.hist(imc_zscore, bins=30)
plt.title("IMC - Z-score")

plt.tight_layout()
plt.savefig("images/imc_normalizacao.png", dpi=150)
plt.close()

# =========================
# 4. BINOMIAL x POISSON
# =========================
plt.figure()
plt.stem(k, pmf_binom, basefmt=" ")
plt.stem(k, pmf_poisson, basefmt=" ")
plt.title("Comparação entre Binomial e Poisson")
plt.xlabel("Número de fumantes em 100 pessoas (k)")
plt.ylabel("PMF")
plt.legend(["Binomial", "Poisson"])
plt.tight_layout()
plt.savefig("images/binomial_poisson.png", dpi=150)
plt.close()

# =========================
# 5. NORMAL x LOG-NORMAL
# =========================
plt.figure(figsize=(10,4))

plt.subplot(1,2,1)
plt.hist(cintura, bins=30)
plt.title("Distribuição Original")

plt.subplot(1,2,2)
plt.hist(cintura_log, bins=30)
plt.title("Distribuição Log-transformada")

plt.tight_layout()
plt.savefig("images/log_normal.png", dpi=150)
plt.close()

print("✅ Todas as imagens foram salvas na pasta 'images' com sucesso.")

