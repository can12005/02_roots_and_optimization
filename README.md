# 02_roots_and_optimization
Homework 2 Comp Mech
[rootms,eams,iterms]=mod_secant(func,xl,xu,es,max);
x=(-10:50);
y=(T/w)*cosh((w/T)*x)+y_0-(T/w);

plot(x,y);
xlabel('X-Dist');
ylabel('Y-Dist');

```Matlab

func=@(x) (x-1)*exp(-(x-1)^2);
dfunc=@(x) exp(-(x-1)^2)*(-2*x^2+4*x-1);
N=5;
x_i=3;
iterations=linspace(1,5,N);
ea=zeros(1,N);
root=zeros(1,N);
for i=1:length(iterations)
    [root(i),ea(i),iter]=newtraph(func,dfunc,x_i,.00001,iterations(i));
end

```Matlab
func=@(x) (x-1)*exp(-(x-1)^2);
dfunc=@(x) exp(-(x-1)^2)*(-2*x^2+4*x-1);
N=5;
x_i=3;
iterations=linspace(1,5,N);
ea=zeros(1,N);
root=zeros(1,N);
for i=1:length(iterations)
    [root(i),ea(i),iter]=newtraph(func,dfunc,x_i,.00000000000001,iterations(i));
end

```Matlab
sigma=2934;
epsilon=2.7e-4;
[goldmin_x0]= goldmin(@(x) lennard_jones(x,sigma,epsilon),2,0,0);
[parabolic_x0]= parabolic (@(x) lennard_jones(x,sigma,epsilon),.1,.4);

```Matlab
sigma=2934;
epsilon=2.7e-4;
x=.3232;
[xmin]=goldmin (@(x) lennard_jones(x,sigma,epsilon),2,0,0);
Etotal= @(dx,F) lennard_jones(xmin+dx,sigma,epsilon)-F.dx;
N=30;
warning('off');
dx=zeros(1,N);
F=linspace(0,.0022,N);
for i=1:N
    optmin=goldmin(@(dx) Etotal(dx,F(i)),-.001,.035);
    dx(i)=optmin;
end
