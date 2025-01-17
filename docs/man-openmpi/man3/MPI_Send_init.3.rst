.. _mpi_send_init:


MPI_Send_init
=============

.. include_body

:ref:`MPI_Send_init` - Builds a handle for a standard send.


SYNTAX
------


C Syntax
^^^^^^^^

.. code-block:: c

   #include <mpi.h>

   int MPI_Send_init(const void *buf, int count, MPI_Datatype datatype,
   	int dest, int tag, MPI_Comm comm, MPI_Request *request)


Fortran Syntax
^^^^^^^^^^^^^^

.. code-block:: fortran

   USE MPI
   ! or the older form: INCLUDE 'mpif.h'
   MPI_SEND_INIT(BUF, COUNT, DATATYPE, DEST, TAG, COMM, REQUEST,
   		IERROR)
   	<type>	BUF(*)
   	INTEGER	REQUEST, COUNT, DATATYPE, DEST, TAG
   	INTEGER	COMM, REQUEST, IERROR


Fortran 2008 Syntax
^^^^^^^^^^^^^^^^^^^

.. code-block:: fortran

   USE mpi_f08
   MPI_Send_init(buf, count, datatype, dest, tag, comm, request, ierror)
   	TYPE(*), DIMENSION(..), INTENT(IN), ASYNCHRONOUS :: buf
   	INTEGER, INTENT(IN) :: count, dest, tag
   	TYPE(MPI_Datatype), INTENT(IN) :: datatype
   	TYPE(MPI_Comm), INTENT(IN) :: comm
   	TYPE(MPI_Request), INTENT(OUT) :: request
   	INTEGER, OPTIONAL, INTENT(OUT) :: ierror


INPUT PARAMETERS
----------------
* ``buf``: Initial address of send buffer (choice).
* ``count``: Number of elements to send (integer).
* ``datatype``: Type of each element (handle).
* ``dest``: Rank of destination (integer).
* ``tag``: Message tag (integer).
* ``comm``: Communicator (handle).

OUTPUT PARAMETERS
-----------------
* ``request``: Communication request (handle).
* ``IERROR``: Fortran only: Error status (integer).

DESCRIPTION
-----------

Creates a persistent communication request for a standard mode send
operation, and binds to it all the arguments of a send operation.

A communication (send or receive) that uses a persistent request is
initiated by the function :ref:`MPI_Start` or :ref:`MPI_Startall`.


ERRORS
------

.. include:: ./ERRORS.rst

.. seealso::
   :ref:`MPI_Bsend_init` :ref:`MPI_Ssend_init` :ref:`MPI_Rsend_init` :ref:`MPI_Recv_init` :ref:`MPI_Start`
   :ref:`MPI_Startall` :ref:`MPI_Request_free`
