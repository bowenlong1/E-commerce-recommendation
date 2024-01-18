UndefinedVariableError: name 'pd' is not defined
---------------------------------------------------------------------------
KeyError                                  Traceback (most recent call last)
File /databricks/python/lib/python3.10/site-packages/pandas/core/computation/scope.py:197, in Scope.resolve(self, key, is_local)
    196 if self.has_resolvers:
--> 197     return self.resolvers[key]
    199 # if we're here that means that we have no locals and we also have
    200 # no resolvers

File /usr/lib/python3.10/collections/__init__.py:986, in ChainMap.__getitem__(self, key)
    985         pass
--> 986 return self.__missing__(key)

File /usr/lib/python3.10/collections/__init__.py:978, in ChainMap.__missing__(self, key)
    977 def __missing__(self, key):
--> 978     raise KeyError(key)

KeyError: 'pd'

During handling of the above exception, another exception occurred:

