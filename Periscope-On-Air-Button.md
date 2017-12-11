The Twitter plugin for WordPress supports adding a `Periscope On Air button <https://www.periscope.tv/embed>`__ to your site through a `WordPress widget <https://codex.wordpress.org/WordPress_Widgets>`__, pasting a Periscope profile URL into post content, or through the ``periscope_on_air`` `WordPress shortcode <http://codex.wordpress.org/Shortcode>`__. Add a Follow button to a WordPress post by
including the shortcode in your post content area or by evaluating a shortcode in PHP using the `do\_shortcode WordPress function <http://codex.wordpress.org/Function_Reference/do_shortcode>`__.

.. raw:: html

   <div><a href="https://www.periscope.tv/twitterdev" class="periscope-on-air">@TwitterDev</a></div>

Display a Periscope On Air button for a Periscope profile URL
-------------------------------------------------------------

Add a Periscope On Air button to a WordPress post by copy-and-pasting a Periscope profile URL on its own line in the post content area.

::

    I broadcast on Periscope.

    https://www.periscope.tv/TwitterDev

    Follow my account to view new broadcasts.

Customize a Periscope On Air button using a shortcode
-----------------------------------------------------

Example:

::

    I broadcast on Periscope.

    [periscope_on_air username="TwitterDev" size="large"]

    Follow my account to view new broadcasts.

Supported shortcode parameters
------------------------------

+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------+
| Attribute    | Description                                                                                                                                                                                                             | Example        |
+==============+=========================================================================================================================================================================================================================+================+
| **username** | Periscope username of the account to display.                                                                                                                                                                           | ``TwitterDev`` |
|              | The plugin will automatically set an omitted ``username`` parameter to the stored Periscope username of the current post author when the shortcode is called inside `the loop <http://codex.wordpress.org/The_Loop>`__. |                |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------+
| size         | Set to ``large`` to display a larger version of the Periscope On Air button.                                                                                                                                            | ``large``      |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------+


Site-wide customization using a filter
--------------------------------------

A website may set site-wide preferences for Periscope On Air buttons by acting on the associative array passed to the ``shortcode_atts_periscope_on_air`` `WordPress filter <http://codex.wordpress.org/Plugin_API#Filters>`__.

Example:

.. code:: php

    /**
     * Always show large button
     *
     * @param array $options parsed options with defaults applied
     * @param array $defaults default values of a Periscope On Air button
     * @param array $attributes user-defined shortcode attributes
     *
     * @return array options array with our customization applied
     */
    function periscope_on_air_custom_options( $options, $defaults, $attributes )
    {
      $options['size'] = 'large';
      return $options;
    }
    add_filter( 'shortcode_atts_periscope_on_air', 'periscope_on_air_custom_options', 10, 3 );
