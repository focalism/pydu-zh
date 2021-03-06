Dict
----

.. py:class:: pydu.dict.AttrDict(seq=None, **kwargs)

  A AttrDict object is like a dictionary except ``obj.foo`` can be used
  in addition to ``obj['foo']``.

    >>> from pydu.dict import AttrDict
    >>> o = AttrDict(a=1)
    o.a
    1
    >>> o['a']
    1
    >>> o.a = 2
    >>> o['a']
    2
    >>> del o.a
    >>> o.a
    Traceback (most recent call last):
     ...    AttributeError: 'a'


.. py:class:: pydu.dict.CaseInsensitiveDict(data=None, **kwargs)

  A case-insensitive ``dict``-like object.
  Implements all methods and operations of ``collections.MutableMapping``
  as well as dict's ``copy``. Also provides ``lower_items``.
  All keys are expected to be strings. The structure remembers the
  case of the last key to be set, and ``iter(instance)``, ``keys()``,
  ``items()``, ``iterkeys()``, and ``iteritems()`` will contain
  case-sensitive keys.

    >>> from pydu.dict import CaseInsensitiveDict
    >>> cid = CaseInsensitiveDict()
    >>> cid['Accept'] = 'application/json'
    >>> cid['aCCEPT'] == 'application/json'
    True
    >>> list(cid) == ['Accept']
    True


.. py:class:: pydu.dict.LookupDict(name=None)

  Dictionary lookup object.

    >>> from pydu.dict import LookupDict
    >>> d = LookupDict()
    >>> d['key']
    None
    >>> d['key'] = 1
    >>> d['key']
    1


.. py:function:: pydu.dict.attrify(obj)

  Attrify obj into ``AttriDict`` or ``list of AttriDict`` if the obj is list.

    >>> from pydu.dict import attrify
    >>> attrd = attrify({
        'a': [1, 2, {'b': 'b'}],
        'c': 'c',
    })
    >>> attrd
    <AttrDict {'a': [1, 2, <AttrDict {'b': 'b'}>], 'c': 'c'}>
    >>> attrd.a
    1
    >>> attrd.a[2].b
    b
    >>> attrd.c
    c
