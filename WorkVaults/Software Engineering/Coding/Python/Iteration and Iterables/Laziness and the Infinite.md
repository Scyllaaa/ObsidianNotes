- Generators only do enough work to produce requested data.
	- Generators are lazy, meaning the computation only happens just in time when the next result is requested. 
- This allows generators to model infinite (or just very large) sequences. 
	- Since values are only produces as requested by the caller, and since no [[data structure]] needs to be built to contain the elements of the sequence. generators can safely be used to produce never-ending or just very large sequences
	- Examples of such sequences are
		- Sensor Readings
		- Mathematical sequences
		- Contents of multi-terabyte files.

