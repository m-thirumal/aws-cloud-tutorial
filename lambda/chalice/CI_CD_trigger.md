# CI/CD for lambda trigger fucntions

Annotate the `lambda_handler(event, context)` with `@app.lambda_function()`

	@app.lambda_function()
	def lambda_handler(event, context):
		logging.info('Event %s', event)
		logging.info('Context %s', context)
		return event;
