# Logging

## Setup
`import logging`
`logging.basicConfig(filename = 'out.log', file mode = 'w', format = '%(name)s - %(level name)s - %(message)s')`

# Logging levels
`logging.debug('Here is the data we received')`
`logging.info('We're starting the function. Nothing unusual.')`
`logging.warning('Something seems strange, so check it out later.')`
`logging.error('There is a problem, but we can keep going.')`
`logging.critical('Something happened, and we have to abort.')`
