=================
DealStat Utilities
=================


.. image:: https://img.shields.io/pypi/v/dealstat.svg
        :target: https://pypi.python.org/pypi/dealstat

.. image:: https://img.shields.io/travis/ecatkins/dealstat.svg
        :target: https://travis-ci.org/ecatkins/dealstat

.. image:: https://readthedocs.org/projects/dealstat/badge/?version=latest
        :target: https://dealstat.readthedocs.io/en/latest/?badge=latest
        :alt: Documentation Status


.. image:: https://pyup.io/repos/github/ecatkins/dealstat/shield.svg
     :target: https://pyup.io/repos/github/ecatkins/dealstat/
     :alt: Updates



DealStat Utilities


* Free software: MIT license

Dealstat
--------
Generic functions that may be moved to specific modules at some point:::

    from dealstat.dealstat import *
    
    # generate random letter based ID of given length
    my_id = unique_id(30)


Boto
--------
Simplifies some of AWS' Boto3 functionality (at the moment, just S3)

* First save `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` as environment variables::

    from dealstat.boto import Boto
    s3 = Boto('s3')

    location1 = {'bucket':'<some-bucket>', 'key': '<some-key'>}
    location2 = {'bucket':'<some-other-bucket>', 'key': '<some-other-key'>}

    # Get temporary pre-signed url
    url = s3.get_temp_url(location1)

    # Move object from one bucket/key to another
    s3.move_object(location1, location2)

    # Upload file
    file_path = '/some/file/path.txt'
    s3.upload_file(file_path, location1)

    # Download file
    destination_file_path = 'local/file/path2.txt'
    s3.download_file(destination_file_path, location2)

    # List contents of bucket
    # Use prefix='some-prefix' to search for specific key prefixes
    # Use exclude_dirs=True to not return directories in result
    s3.list_bucket('<some-bucket'>, prefix=None, exclude_dirs=True)

Machine Learning
--------
Random utilities useful in ML prototyping

* Download and use Standform NLP Glove Embedings ::

    from dealstat.ml import Embeddings
    
    Embed = Embeddings()
    
    # Download embeddings
    Embed.download_embeddings()
    
    # Unzip embeddings
    Embed.extract_embeddings()
    
    # Generate embeddings look up dict for given dimension
    dim = 200
    embedding_dict = Embed.generate(loc='.', dim=dim)
    
    



Credits
-------

This package was created with Cookiecutter_ and the `audreyr/cookiecutter-pypackage`_ project template.

.. _Cookiecutter: https://github.com/audreyr/cookiecutter
.. _`audreyr/cookiecutter-pypackage`: https://github.com/audreyr/cookiecutter-pypackage
