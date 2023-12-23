def getRREF(matrix, row, col,cc):
    for r in range(0, row):
        i=r
        while matrix[i][cc] == 0:
            i=i+1
            if i==row:
                i=r
                cc=cc+1
                if cc==col:
                    return matrix
        
        matrix = interchange(matrix, i, r)
        
        if matrix[r][cc] != 0:
            matrix = div(matrix, r, matrix[r][cc])
        for i in range(0, row):
            if i != r:
                cs = getfactor(matrix, cc, i, r)
                matrix = replacement(matrix, i, col, cs, r)            
        cc=cc+1
        if cc>=col:
            return matrix
    return matrix
def div(matrix,x,y):
    matrix[x]=[ele/y for ele in matrix[x]]
    return matrix
def getfactor(matrix, cc, rownumber1, rownumber2):
    cs = -1*matrix[rownumber1][cc]/matrix[rownumber2][cc]
    return cs
def replacement(matrix,rownumber1,col,cs,rownumber2):
    for j in range(col):
        matrix[rownumber1][j]=matrix[rownumber1][j]+cs*matrix[rownumber2][j]
    return matrix
def interchange(matrix,row1,row2):
    matrix[row1],matrix[row2]=matrix[row2],matrix[row1]
    return matrix
def pivotpos(matrix):
    c1=[]
    r1=[]
    k=0
    for g in range(col):
        if matrix[k][g]!=0:
            c1.append(g)
            r1.append(k)            
            if k>=row-1:
                break
            k+=1
    pc=list(zip(r1,c1))
    return pc
def free(col,pivcor):
    all=[val for val in range(col)]
    pc=[p[1] for p in pivcor] 
    npc=[]
    for elem in all:
        if elem not in pc:
            npc.append(elem)
    return npc
def parametric(matrix,row,col,npc,pivcor):
    l=[]
    for values in npc:
        m=[]
        for cn in range(col):         
            if cn==values:
                m.append(1)
            elif cn in [y for x, y in pivcor]:
                for x,y in pivcor:
                    if cn == y:
                        m.append(-1*matrix[x][values])
            else:
                m.append(0)         
        l.append(m)
    return l
def roundm(matrix):
    for e in range(len(matrix)):
        for j in range(len(matrix[e])):
            if abs(matrix[e][j])<10**-5:
                matrix[e][j]=0.0
    return matrix
    
# input of matrix
matrix=[]
row=int(input("Enter number of rows: "))
col=int(input("Enter number of columns: "))
for i in range(row):
    r=list(map(int,input().split()))
    matrix.append(r)

cc=0
matrix=getRREF(matrix, row, col,cc)
matrix=roundm(matrix)
print("RREF:")
for v in range(row):
    print(matrix[v])   

pivcor=pivotpos(matrix)
if len(pivcor)==col:
    print("The system has a trivial solution")    
else:
    print("The system has non-trivial solution")
    fv=free(col,pivcor)
    ps=parametric(matrix,row,col,fv,pivcor)
    ans=list(zip(fv,ps))
    for answers in ans:
        print("x",int(answers[0])+1,"*",answers[1],"+",end="",sep="")
