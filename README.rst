=================================
Leaderboard: redis backed leaderboard library
=================================

:Version: 1.1.6
:Download: http://pypi.python.org/pypi/leaderboard
:Source: https://github.com/agoragames/python-leaderboard
:Keywords: python, redis, leaderboard

.. contents::
    :local:

.. _pthon-leaderboard-overview:

Overview
========

Leaderboards backed by Redis in Python, http://redis.io.

Builds off ideas proposed in http://blog.agoragames.com/2011/01/01/creating-high-score-tables-leaderboards-using-redis/.

see https://github.com/agoragames/leaderboard/ for detailed usage information

For other platforms see:

+ Ruby - https://github.com/agoragames/leaderboard
+ Python - https://github.com/agoragames/python-leaderboard
+ Java - https://github.com/agoragames/java-leaderboard
+ Scala - https://github.com/agoragames/scala-leaderboard
+ PHP - https://github.com/agoragames/php-leaderboard
+ Erlang - https://github.com/agoragames/erlang-leaderboard
+ NodeJS - https://github.com/omork/node-leaderboard


.. _license:

License
=======

This software is licensed under the `New BSD License`. See the ``LICENSE``
file in the top distribution directory for the full license text.

.. # vim: syntax=rst expandtab tabstop=4 shiftwidth=4 shiftround

Installation
============

Add 'leaderboard' folder to your path or issue 'pip install leaderboard'.

Usage
=====

Creating a leaderboard
----------------------

Be sure to require the leaderboard library:

``from sth``


``from leaderboard import Leaderboard``


Create a new leaderboard or attach to an existing leaderboard named 'highscores':

``
highscore_lb = Leaderboard('highscores')
``

Ranking members in the leaderboard
----------------------------------

Add members to your leaderboard using rank_member:

for x in range(0, 10):
        highscore_lb.rank_member("member_#%s" % x, x)

You can call rank_member with the same member and the leaderboard will be updated automatically.

``highscore_lb.total_members``
    
Retrieving members from the leaderboard
---------------------------------------

Get page 1 in the leaderboard:

Get some information about your leaderboard:

``highscore_lb.total_members()``
``highscore_lb.total_pages()``

The `rank_member` call will also accept an optional hash of member data that could
be used to store other information about a given member in the leaderboard. This
may be useful in situations where you are storing member IDs in the leaderboard and
you want to be able to store a member name for display. Example:

``highscore_lb.rank_member('84849292', 1, username='member_name')``

Retrieving members from the leaderboard
---------------------------------------

Get page 1 in the leaderboard:

``highscore_lb.leaders(1)``

You can pass various options to the calls `leaders`, `around_me` and `ranked_in_list`.
Valid options are `:with_scores`, `:with_rank`, `:with_member_data`, `:use_zero_index_for_rank`
and `:page_size`. Below is an example of retrieving the first page in the leaderboard
without ranks:

``highscore_lb.leaders(1, with_rank=False)``