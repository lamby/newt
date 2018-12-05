project('newt', 'c')

flex = find_program('flex')
bison = find_program('bison')

lgen = generator(flex,
		 output : '@PLAINNAME@.c',
		 arguments : ['-o', '@OUTPUT@', '@INPUT@'])

pgen = generator(bison,
		 output : ['@BASENAME@.c', '@BASENAME@.h'],
		 arguments : ['@INPUT@', '--defines=@OUTPUT1@', '--output=@OUTPUT0@'])

lfiles = lgen.process('newt-lex.l')
pfiles = pgen.process('newt-gram.y')

conf_data = configuration_data()
configure_file(output : 'config.h',
	       configuration : conf_data)

cfiles=[
  'newt-code.c',
  'newt-frame.c',
  'newt-list.c',
  'newt-main.c',
  'newt-memory.c',
  'newt-name.c',
  'newt-poly.c'
]

executable('newt', cfiles, lfiles, pfiles)