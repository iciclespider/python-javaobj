javaobj-py3
###########

.. image:: https://img.shields.io/pypi/v/javaobj-py3.svg
    :target: https://pypi.python.org/pypi/javaobj-py3/
    :alt: Latest Version

.. image:: https://img.shields.io/pypi/l/javaobj-py3.svg
    :target: https://pypi.python.org/pypi/javaobj-py3/
    :alt: License

.. image:: https://travis-ci.org/tcalmant/python-javaobj.svg?branch=master
     :target: https://travis-ci.org/tcalmant/python-javaobj
     :alt: Travis-CI status

.. image:: https://coveralls.io/repos/tcalmant/python-javaobj/badge.svg?branch=master
     :target: https://coveralls.io/r/tcalmant/python-javaobj?branch=master
     :alt: Coveralls status

python-javaobj is a python library that provides functions for reading and
writing (writing is WIP currently) Java objects serialized or will be
deserialized by _ObjectOutputStream_. This form of object representation is a
standard data interchange format in Java world.

javaobj module exposes an API familiar to users of the standard library
marshal, pickle and json modules.

About this repository
=====================

This project is a fork of python-javaobj by Volodymyr Buell, originally from
`Google Code <http://code.google.com/p/python-javaobj/>`_ and now hosted on
`GitHub <https://github.com/vbuell/python-javaobj>`_.

This fork intends to work both on Python 2.7 and Python 3.2+.

Features
========

* Java object instance unmarshaling
* Java classes unmarshaling
* Primitive values unmarshaling
* Automatic conversion of Java Collections to python ones
  (_HashMap_ => dict, _ArrayList_ => list, etc)

Requirements
============

* Python >= 2.7 or Python >= 3.2
* Maven 2+ (for building test data of serialized objects.
  You can skip it if you do not plan to run tests.py)

Usage
=====

Unmarshalling of Java serialised object:

.. code-block:: python

    import javaobj

    jobj = self.read_file("obj5.ser")
    pobj = javaobj.loads(jobj)
    print(pobj)

Or, you can use Unmarshaller object directly:

.. code-block:: python

    import javaobj

    marshaller = javaobj.JavaObjectUnmarshaller(open("objCollections.ser"))
    pobj = marshaller.readObject()

    self.assertEqual(pobj.value, 17)
    self.assertTrue(pobj.next)

    pobj = marshaller.readObject()
