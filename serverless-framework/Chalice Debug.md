##  AWS Chalice Application Debug

AWS Chalice is a Python micro-framework, designed to provide developers with a familiar flask-like experience when developing serverless applications.

#### Debug locally

    chalice local
  
### Debug with PyCham

    chalice local --no-autoreload
  
  In PyCharm, go to the `Run` menu and choose the option `Attach to Process`….
  
A new menu will open, the menu lists all python processes. Select the chalice local process to attach a debugger to it.


##Troubleshoot

Deploy `timeout`

    chalice deploy --connection-timeout 120
