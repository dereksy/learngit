import asyncio
async def outer():
    print('in outer')
    print('waiting for result1')
    result1 = await phase1()
    print('waiting for result2')
    result2 = await phase2(result1)
    return (result1,result2)

async def phase1():
    print('in phase1')
    return 'result1'

async def phase2(arg):
    rint('in phase2')
    return 'result2 derived from {}'.format(arg)

if __name__=="__main__":
   loop = asyncio.get_event_loop()
   tasks = [outer()]
   return_value = loop.run_until_complete(asyncio.wait(tasks))
   print(return_value)
