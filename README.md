# SolutionForQueenProblem
Solution for the 8 Queens puzzle in python https://en.wikipedia.org/wiki/Eight_queens_puzzle

##Rodrigo Maranduba Urso
def GravaTabuleiro():
    S = " "
    for j in range(Tam-1):
        S = S + "-----"
    S = S + "---- "
    arq.writelines(S+"\n")
    for i in range(Tam):
        S = "| "
        for j in range(Tam):
            if tab[i][j]!=0 :
                S = S + "  " + " | "
            else:
                S = S + " R" + " | "
        arq.writelines(S+"\n")
        if i < Tam-1:
            S = "|"
            for j in range(Tam-1):
                S = S + "----+"
            S = S + "----|"
            arq.writelines(S+"\n")
    S = " "
    for j in range(Tam-1):
        S = S + "-----"
    S = S + "---- "
    arq.writelines(S+"\n") 
def imprimirtab():
    print(" --------------------------------------- ")
    for i in range(8):
        print "|",
        for j in range(8):
            if tab[i][j]<10:
                print "",
                print tab[i][j],
            else:
                print tab[i][j],
            print "|",
        print
        if i <7:
            print(" ----+----+----+----+----+----+----+---- ")
        else:
            print(" --------------------------------------- ")
def verificarcoluna(coluna):
    verifica=[100,100,100,100,100,100,100,100]
    for i in range(8):
        for j in range(8):
            if tab[i][j]==0:
                verifica[j]=99
    if verifica[coluna]==100:
        return("s")
    else:
        return("n")
def verificardiagonal(linha,coluna):
    xs=linha
    xd=linha
    y1=coluna
    y2=coluna
    yne=coluna
    ypos=coluna
    control=0
    while xs>0:
        xs=xs-1
        if yne>0:
            yne=yne-1
            if tab[xs][yne]==0:
                control=1
                return("n")
        if ypos<7:
            ypos=ypos+1
            if tab[xs][ypos]==0:
                control=1
                return("n")
    while xd<7:
        xd=xd+1
        if y1>0:
            y1=y1-1
            if tab[xd][y1]==0:
                control=1
                return("n")
        if y2<7:
            y2=y2+1
            if tab[xd][y2]==0:
                control=1
                return("n")
    if control==0:
        return("s")
def zeratab():
    numerais=1
    for i in range(8):
        tab.append([])
        for j in range(8):
            tab[i].append(numerais)
            numerais=numerais+1
arq = open('Solucoes.txt', 'w')
Tam = 8
zeta=0
contando=0
mudanca=0
sol=[]
saber=0
h=0
varia=0
sinal=0
i=[0,1,2,3,4,5,6,7]
iindice=0
while h<8 and iindice<8 :
    j=[0,0,0,0,0,0,0,0]
    j[h]=varia
    if mudanca!=h:
        j[mudanca]=zeta
    i=[0,1,2,3,4,5,6,7]
    contando=0
    tab=[]
    zeratab()
    while i[iindice]<8:
        while j[i[iindice]]<8:
            s=j[i[iindice]]
            if sinal==1:
                s=7-j[i[iindice]]
            checacoluna=verificarcoluna(s)
            checadiagonal=verificardiagonal(i[iindice],s)
            if checacoluna=="s" and checadiagonal=="s" and (0 not in tab[i[iindice]]):
                tab[i[iindice]][s]=0
            j[i[iindice]]=j[i[iindice]]+1
        i[iindice]=i[iindice]+1
    if iindice>0:
        anindice=iindice-1
        while anindice>=0:
            jotinha=0
            while jotinha<8:
                checacoluna=verificarcoluna(jotinha)
                checadiagonal=verificardiagonal(anindice,jotinha)
                if checacoluna=="s" and checadiagonal=="s" and (0 not in tab[anindice]):
                    tab[anindice][jotinha]=0
                jotinha=jotinha+1
                saber=saber+1
            anindice=anindice-1
    zeta=zeta+1       
    if zeta==8:
        zeta=1
        mudanca=mudanca+1
    for conta in range(0,8,1):
        contando=contando+(tab[conta].count(0))
    if contando==8:
        igualdade=0
        for ig in range(len(sol)):
            if sol[ig]==tab:
                igualdade=1
        if igualdade==0:
            sol.append(tab)
            imprimirtab()
            GravaTabuleiro()
    saber=saber+1
    if mudanca==8:
        varia=varia+1
        mudanca=0
        if varia==8:
            h=h+1
            varia=0
    if h==8:
        zeta=0
        mudanca=0
        h=0
        varia=0
        if sinal==1:
            h=8
        sinal=1
    if h==8:
        iindice=iindice+1
        zeta=0
        mudanca=0
        h=0
        varia=0
        sinal=0
    if iindice==8:
        h=8       
zeta=0
mudanca=0
h=0
varia=0
sinal=0
iindice=7
while h<8 and iindice>=0 :
    j=[0,0,0,0,0,0,0,0]
    j[h]=varia
    if mudanca!=h:
        j[mudanca]=zeta
    i=[0,1,2,3,4,5,6,7]
    contando=0
    tab=[]
    zeratab()
    while i[iindice]>=0:
        while j[i[iindice]]<8:
            s=j[i[iindice]]
            if sinal==1:
                s=7-j[i[iindice]]
            checacoluna=verificarcoluna(s)
            checadiagonal=verificardiagonal(i[iindice],s)
            if checacoluna=="s" and checadiagonal=="s" and (0 not in tab[i[iindice]]):
                tab[i[iindice]][s]=0
            j[i[iindice]]=j[i[iindice]]+1
        i[iindice]=i[iindice]-1
    if iindice<7:
        anindice=iindice+1
        while anindice<8:
            jotinha=0
            while jotinha<8:
                checacoluna=verificarcoluna(jotinha)
                checadiagonal=verificardiagonal(anindice,jotinha)
                if checacoluna=="s" and checadiagonal=="s" and (0 not in tab[anindice]):
                    tab[anindice][jotinha]=0
                jotinha=jotinha+1
                saber=saber+1
            anindice=anindice+1
    zeta=zeta+1       
    if zeta==8:
        zeta=1
        mudanca=mudanca+1
    for conta in range(0,8,1):
        contando=contando+(tab[conta].count(0))
    if contando==8:
        igualdade=0
        for ig in range(len(sol)):
            if sol[ig]==tab:
                igualdade=1
        if igualdade==0:
            sol.append(tab)
            imprimirtab()
            GravaTabuleiro()
    saber=saber+1
    if mudanca==8:
        varia=varia+1
        mudanca=0
        if varia==8:
            h=h+1
            varia=0
    if h==8:
        zeta=0
        mudanca=0
        h=0
        varia=0
        if sinal==1:
            h=8
        sinal=1
    if h==8:
        iindice=iindice-1
        zeta=0
        mudanca=0
        h=0
        varia=0
        sinal=0
    if iindice==-1:
        h=8
arq.close()
print("A quantidade de solucoes encontradas foi: ")
print(len(sol))
