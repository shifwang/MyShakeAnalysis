# EDA logs:

Oct 24:

ISSUE #1, The provided read data function has a bug: it errors when executing the following:

    data = json.load(open('./EQ/shake_table/trial142_phone3.json', 'rb'))

    t, x, y, z = get_data(data)

    plot_data(t, x, y, z)

The problem is because t and x does not have the same length, which is because of the way how t is generated (using arange).

2, Somehow we could shrink the storage by truncating all the numerics or using formats other than json. 
The goal is to fit it in the github repo.
