For access to the front end of this application, please follow this link: https://fintech-market-analysis-kandupay.anvil.app/

Once on the landing page, choose the sending and receiving countries based on the numbered list on the page and discover if the market channel combination is ripe for market targeting for a fintech remittance platform.

-----------------BREAK-------------------

>>>Code for the front-end system is as follows>>>

from ._anvil_designer import Form1Template
from anvil import *
import anvil.server
import anvil.tables as tables
import anvil.tables.query as q
from anvil.tables import app_tables


class Form1(Form1Template):
  def __init__(self, **properties):
    # Set Form properties and Data Bindings.
    self.init_components(**properties)    

    # Any code you write here will run before the form opens.
  
  def analyze_channel_click(self, **event_args):
    """This method is called when the button is clicked"""
    channel_analysis = anvil.server.call('predict_channel',
                                       self.sending_country.text,
                                       self.receiving_country.text)
    if channel_analysis:
      self.channel_assessment.visible = "1"
      self.channel_assessment.text = "The channel is a strong match for remittance fintech market targeting."
    
    
