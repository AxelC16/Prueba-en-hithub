# Prueba-en-hithub

#include <stdio.h>
#include <stdlib.h>
double **memoriaMatriz (int n, int m){
  double **mat;
  int i;
  
  mat= (double **) calloc (n, sizeof (double*));
  for (i=0; i<n; i++)
       mat[i]= (double *) calloc (m, sizeof (double));	
}
void imrprimeMatriz (double **mat, int n, int m){
	int i,j;
	
	for(i=0; i<n; i++){
	for(j=0; j<m; j++)
      	printf("%lf\t",mat[i][j]);
      	printf("\n");	
	}
	  
      
}

void leeMatriz (double **mat, int n, int m){
	int i,j;
	
	for(i=0; i<n; i++)
	  for(j=0; j<m; j++)
      {
      	printf("Elemento %d,%d: ",i+1,j+1);
      	scanf("%lf",&mat[i][j]);
      }
}
void eliminacionGaussiana (double **a, double *b, int n ){
	int i,j,k;
	double cte; // Para determinar la constante
	
	for (i=0; i< n; i++){
	 for (j=i+1; j<n ; j++){
	 cte= a[j][i]/a[i][i];
	 for (k=i; k<n; k++)
	      a[j][k] = a[j][k] - cte*a[i][k];  	
}			
}
}


int main () {
	int n,i;
	double **a,*b,*x;
	
	printf("Numero de ecuaciones: ");
	scanf("%d",&n);
	a= memoriaMatriz (n,n);
	b= (double *) calloc (n,sizeof (double));
	printf ("Matriz de coeficientes: \n");
	leeMatriz (a,n,n);
	printf("Terminos independientes: \n");
	for (i=0; i<n; i++){
		printf("Elemento %d: ",i);  
		scanf ("%lf",&b[i]);	
	}
	eliminacionGaussiana (a,b,n);
	printf ("Matriz triangulada\n");
	imprimeMatriz (a,n,n);
	
	
}
