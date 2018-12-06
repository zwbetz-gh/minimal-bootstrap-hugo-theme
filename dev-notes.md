# Dev Notes

To build the example site against the theme locally:

```
hugo server \
--gc \
--source exampleSite \
--config exampleSite/config.toml \
--themesDir ../.. \
--theme minimal-bootstrap-hugo-theme \
--renderToDisk
```